---
title: Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: cc60ee32efcbe1e6ac1ce620fa1c17504db5197f
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690578"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład

Rozszerzona ochrona jest inicjatywy zabezpieczeń, aby zapewnić ochronę przed ataków typu man-in--middle (MITM) ataków, w których osoba atakująca ("man-in--middle") przechwytuje poświadczenia klienta i są one używane do dostępu do bezpiecznych zasobów na serwerze zamierzonego klienta.

Aby uzyskać więcej informacji, zobacz [ochrona rozszerzona na potrzeby uwierzytelniania Przegląd](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).

> [!NOTE]
> Ten przykład działa tylko w przypadku hostowania w usługach IIS. Go nie działa na serwerze programowania w usłudze Visual Studio, ponieważ nie obsługuje protokołu HTTPS.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Instalowanie usług IIS na komputerze, z poziomu apletu Dodaj/Usuń programy -> Funkcje Windows.

2. Włącz uwierzytelnianie Windows w funkcji Windows: Internetowe usługi informacyjne -> sieci World Wide Web Services -> Zabezpieczenia -> uwierzytelniania Windows.

3. Włącz aktywację HTTP w funkcji Windows: Microsoft .NET Framework 3.5.1 -> Aktywacja HTTP programu Windows Communication Foundation.

4. Ten przykładowy skrypt wymaga klienta do nawiązania bezpiecznego kanału z serwerem i dlatego wymaga obecności certyfikatu serwera, które mogą być instalowane z Menedżera usług Internet Information Services (IIS).

    1. Otwórz Menedżera usług IIS -> certyfikatów serwera (na karcie Widok funkcji).

    2. Na potrzeby testowania w tym przykładzie, można utworzyć certyfikatu z podpisem własnym. (Jeśli nie chcesz, aby program Internet Explorer będzie wyświetlany monit o certyfikat nie jest bezpieczne, można zainstalować go w magazynie zaufanego certyfikatu głównego urzędu).

5. Przejdź do okienka akcji dla domyślnej witryny sieci Web. Kliknij przycisk Edytuj lokacji -> powiązania. Dodaj HTTPS jako typ, jeśli nie jest jeszcze obecne, numer portu 443 i przypisz certyfikat SSL utworzony w kroku powyżej.

6. Tworzenie usługi. Tworzy katalog wirtualny w usługach IIS (z akcji po kompilacji, określony we właściwościach projektu) i kopiuje pliki dll, .svc i konfiguracja stosownie do potrzeb dla usługi, aby być hostowana w sieci Web.

7. Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalog wirtualny (ExtendedProtection), który został utworzony w poprzednim kroku, a następnie wybierz konwersji do aplikacji.

8. Otwórz moduł uwierzytelniania w Menedżerze usług IIS dla tego katalogu wirtualnego, a następnie włączyć uwierzytelnianie Windows.

9. Otwórz Zaawansowane ustawienia dla Windows uwierzytelniania dla tego katalogu wirtualnego i ustaw ją na wymagane, ponieważ w tym przykładzie odpowiednie ustawienia ExtendedProtection jest ustawiona na zawsze.

10. Można testować usługę, uzyskując dostęp do adresu URL w oknie przeglądarki. Jeśli chcesz uzyskać dostęp do tego adresu URL z wielu maszyn, upewnij się, że Zapora jest otwarta dla wszystkich połączeń przychodzących HTTP i HTTPS.

11. Otwórz plik konfiguracji klienta i podaj nazwę maszyny pełną \<klienta >- \<punktu końcowego >-atrybut adresu zastępowanie \<full_machine_name >.

12. Uruchom klienta. Klient komunikuje się z usługą przez ustanowienie bezpiecznego kanału i używanie rozszerzonej ochrony w sposób niewidoczny.
