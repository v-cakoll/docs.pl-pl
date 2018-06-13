---
title: Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d45271180b7f00ba78d106f2a93d5860375da5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495083"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład
Ochrona rozszerzona jest inicjatywą zabezpieczeń do ochrony przed man-in--middle (MITM) ataków, w których osoba atakująca ("man-in--middle") przechwytuje poświadczenia klienta i używa ich do uzyskiwania dostępu bezpiecznych zasobów na serwerze danego klienta.  
  
 Aby uzyskać więcej informacji, zobacz [ochrona rozszerzona na potrzeby uwierzytelniania omówienie](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  W tym przykładzie działa tylko w przypadku, gdy hostowanych w usługach IIS. On nie działać na serwera wdrożeniowego Visual Studio, ponieważ nie obsługuje protokołu HTTPS.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj usługę IIS na komputerze z apletu Dodaj/Usuń programy -> Funkcje systemu Windows.  
  
2.  Włącz uwierzytelnianie systemu Windows w funkcji systemu Windows: Internetowe usługi informacyjne -> usługi sieci World Wide Web -> Zabezpieczenia -> uwierzytelniania systemu Windows.  
  
3.  Włącz aktywację HTTP w funkcji systemu Windows: Microsoft .NET Framework 3.5.1 -> Aktywacja HTTP programu Windows Communication Foundation.  
  
4.  W tym przykładzie wymaga klienta do ustanowienia bezpiecznego kanału z serwerem i dlatego wymaga obecności certyfikat serwera, które można zainstalować z programu Internet Information Services (IIS) Manager.  
  
    1.  Otwórz Menedżera usług IIS -> certyfikatów serwera (na karcie Widok funkcji).  
  
    2.  Na potrzeby testowania w tym przykładzie, można utworzyć certyfikatu z podpisem własnym. (Jeśli nie chcesz, aby program Internet Explorer będzie wyświetlany monit o certyfikat nie jest bezpieczne, można zainstalować go w magazynie zaufanego certyfikatu głównego urzędu).  
  
5.  Przejdź do okienka Akcje dla domyślnej witryny sieci Web. Kliknij przycisk Edytuj lokacji -> powiązania. Dodaj HTTPS jako typ, jeśli nie jest już istnieje z numerem portu 443 i przypisz certyfikat SSL utworzony w kroku powyżej.  
  
6.  Tworzenie usługi. Tworzy katalog wirtualny w usługach IIS (z akcji kompilacji po określonej we właściwościach projektu) i kopiuje pliki dll, SVC i config zgodnie z potrzebami dla usługi, aby być hostowana w sieci Web.  
  
7.  Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalogu wirtualnego (ochrona rozszerzona), który został utworzony w poprzednim kroku, a następnie wybierz konwersji do aplikacji.  
  
8.  Otwórz moduł uwierzytelniania w Menedżerze usług IIS dla tego katalogu wirtualnego, a następnie włączyć uwierzytelnianie systemu Windows.  
  
9. Otwórz Zaawansowane ustawienia dla uwierzytelniania systemu Windows dla tego katalogu wirtualnego i ustaw ją na wymagane, ponieważ w przykładzie odpowiednie ustawienie Ochrona rozszerzona ma wartość Always.  
  
10. Można testować usługę, uzyskując dostęp do adresu URL z okna przeglądarki. Aby uzyskać dostęp do tego adresu URL z krzyżowego maszyny, upewnij się, że zapory jest otwarty dla wszystkich połączeń przychodzących HTTP i HTTPS.  
  
11. Otwórz plik konfiguracji klienta i podaj nazwę maszyny pełne \<klienta >- \<punktu końcowego > — atrybut adresu, zastępując << full_machine_name >>.  
  
12. Uruchom klienta. Klient komunikuje się z usługą ustanowienie bezpiecznego kanału i używając ochrona rozszerzona w tle.
