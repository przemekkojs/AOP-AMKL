# AOP-AMKL
Projekt Arkusza Organizacji Pracy dla Akademii Muzycznej im. Karola Lipińskiego we Wrocławiu.

## 1. Wstęp
Dotychczasowe rozwiązanie - każdy z Dziekanów pracował na osobnym pliku .xlsx (programu Microsoft Excel). Było to niespójne, nieefektywne oraz wprowadzało chaos i trudności w nauce dla nowych pracowników. Pierwszym pomysłem było uspójnienie tego pliku dla każdego z wydziałów oraz wzbogacenie go o formuły, zapewniające automatyczne sumowanie oraz zmniejszenie błedu ludzkiego.

Moim zdaniem jednak - na dłuższą metę, takie rozwiązanie będzie nieefektywne. Obliczeń jest bardzo dużo, przy wszystkich studentach i pracownikach mówimy o tysiącach wierszy oraz -nastu tysiącach formuł.

Powstał mi zatem w głowie - praktycznie od razu, gdy usłyszałem o problemie - pomysł na narzędzie, które rozwiąże to wszystko, będzie działać niezależnie, jednocześnie będąc w dalszym ciągu kompatybilnym z programem Excel (oczywiście, z zastosowaniem formatu .csv).

## 2. Założenia
Aby projekt był kompletny, skalowalny oraz możliwie bezawaryjny i przyszłościowy - narzuciłem sobie pewne założeniam wymienione poniżej.

1. Postawienie na darmowe rozwiązania - Git Hub Pages oraz baza danych Supabase. Zapewni to darmowy, statyczny hosting oraz umożliwi pracę w czasie rzeczywistym dla wielu użytkowników na raz.

2. System czasu rzeczywistego - wszelkie zmiany będą odnosiły natychmiastowe skutki.

3. Autoryzacja - ze względu na publiczność projektu, konieczna będzie pewnego rodzaju autoryzacja, aby niepowołane osoby nie mogły nic zmieniać w bazie danych. **Jedyna alternatywa to hosting na jakimś wewnętrznym serwerze AMKL**. Istnieje kilka rozwiązań, przebadam które będzie najbardziej odpowiednie.

4. Kompatybilność z formatem .csv - do przeprowadzania wydruków, transferu danych, archiwizacji itp. Zapewni to również kompatybilność z programem Excel - na przykład do pokazania danych innym osobom, bez dawania dostępu do aplikacji.

5. Uproszczenie procesu - koniec z wieloma niezrozumiałymi polami, kolumnami, powielaniem danych itp. System będzie po prostu intuicyjny.

## 3. Ograniczenia
Niestety, ze względu na darmowość rozwiązania, część potencjalnych funkcjonalności może się okazać niemożliwa bądź trudna do zrealizowania.

1. Działanie live dla wielu użytkowników - technologia tzw. WebSocket-ów (zapewniająca stałe połączenie między klientem a serwerem, pozwalająca na ciągłą komunikację) - może generować koszty użycia, jest to jednak jeszcze temat do zbadania.

2. Aplikacja musi zostać zaprojektowana **kompletnie** - oznacza to, że wszelkie sprawy związane z jej działaniem muszą zostać opisane szczegółowo od samego początku, żeby było jasne, czego właściwie potrzeba. Jeżeli coś nie zostanie uwzględnione na samym początku, to dodanie tego później może rodzić pewne problemy.

## 4. Architektura (dla zainteresowanych)
Architektura serverless, z Database-as-backend. Pozwoli to na statyczny hosting na GitHub pages. Baza danych pełni rolę database oraz back-endu jednocześnie. Nie mamy zatem kosztów utrzymania hostingu chmurowego.

### Frontend
Blazor WebAssembly - kompilowany do statycznych plików *HTML* + *JS*, zatem hosting statyczny jak najbardziej wchodzi tutaj w grę

### Backend
Brak, formę back-endu pełni Supabase

### Baza danych
Supabase - [link](https://supabase.com)

## 5. Analiza kosztów
Generalnie, z aplikacji będzie korzystać mała ilość osób, zatem ruchu ani obciążenia wysokiego nie będzie. W połączeniu z darmowym hostingiem **prawdopodobnie** będzie to aplikacja darmowa. Dla porządku zamieszczam szczegóły. [Supabase/pricing - zakładka free](https://supabase.com/pricing).
- Nielimitowane API (to bardziej dla mnie informacja)
- 50 000 użytkowników
- 500 MB danych (dla naszego przypadku oceniam zużycie na poziomie maks 2 MB, zatem 0.4%)
- 5 GB danych przesyłanych
- 1 GB luźnych danych
- **MINUS** - po tygodniu nieaktywności projektu baza jest zatrzymywana, a jej ponowne uruchomienie chwilę zajmuje.

Zatem, przy odpowiednim wykorzystaniu - wszystko będzie kompletnie bezkosztowe oraz sprawne w działaniu.

© Przemysław Kojs 2025