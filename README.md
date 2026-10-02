# Agenda de contacte

Proiect individual la disciplina Metode avansate de programare, anul universitar 2026-2027.

## Autor

- **Nume:** Vîrtic Răzvan-Cosmin-Cristian
- **Grupa:** 2.2
- **Marca:** LH715719
- **Tema:** 1 - Agenda de contacte

## Descriere

Aplicatia este un serviciu web care gestioneaza o agenda de contacte. Permite adaugarea, listarea, cautarea si stergerea contactelor prin cereri HTTP, iar datele sunt pastrate in memorie. Serviciul ruleaza intr-un container Docker si este publicat automat in GitHub Container Registry.

## Tehnologii

C++20 cu cpp-httplib si nlohmann/json

## Rulare

```
docker build -t map-proiect .
docker run -d -p 8080:8080 map-proiect
```

Aplicatia asculta pe portul 8080. Verificati:

```
curl http://localhost:8080/health
curl http://localhost:8080/version
```

## Testare

```
cmake -B build -DBUILD_TESTS=ON
cmake --build build -j
./build/tests
```

## Rutele implementate

| Ruta | Metoda | Descriere |
|---|---|---|
| `/health` | GET | Starea serviciului |
| `/version` | GET | Versiunea si commit-ul din care a fost construita imaginea |
| `/` | GET | Pagina de prezentare |
| `/reset` | POST | Goleste datele din memorie |
| `/contacts` | POST | Adauga un contact (in curs de implementare) |

## Decizii de implementare

Deocamdata au fost pastrate deciziile din scheletul cursului: datele sunt stocate in memorie, in clasa `Store`, protejata cu mutex, iar logica pura se afla in `app.hpp`, separata de rutele HTTP din `main.cpp`, ca sa poata fi testata fara a porni serverul. Deciziile specifice temei vor fi adaugate pe masura ce sunt implementate rutele.