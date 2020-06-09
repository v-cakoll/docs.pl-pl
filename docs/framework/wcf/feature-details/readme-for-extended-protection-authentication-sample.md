---
title: Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601104"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład

Ochrona rozszerzona to inicjatywa zabezpieczeń chroniąca przed atakami typu man-in-the-Middle (MITM), w których osoba atakująca ("man-in-the-middle") przechwytuje poświadczenia klienta i używa ich do uzyskiwania dostępu do zabezpieczonych zasobów na zamierzonym serwerze klienta.

Aby uzyskać więcej informacji, zobacz [Ochrona rozszerzona uwierzytelniania przegląd](extended-protection-for-authentication-overview.md).

> [!NOTE]
> Ten przykład działa tylko w przypadku hostowania w usługach IIS. Nie działa na serwerze deweloperskim programu Visual Studio, ponieważ nie obsługuje protokołu HTTPS.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj usługi IIS na maszynie za pomocą apletu Dodaj/Usuń programy — > funkcje systemu Windows.

2. Włącz uwierzytelnianie systemu Windows w funkcjach systemu Windows: Internet Information Services > World Wide Web Services — > zabezpieczenia-> uwierzytelniania systemu Windows.

3. Włącz aktywację HTTP w funkcjach systemu Windows: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation Aktywacja HTTP.

4. Ten przykład wymaga od klienta ustanowienia bezpiecznego kanału z serwerem i dlatego wymaga obecności certyfikatu serwera, który można zainstalować z Menedżera Internet Information Services (IIS).

    1. Otwórz Menedżera usług IIS — > certyfikaty serwera (z karty Widok funkcji).

    2. Na potrzeby testowania tego przykładu można utworzyć certyfikat z podpisem własnym. (Jeśli nie chcesz, aby program Internet Explorer monitował o certyfikat, który nie jest zabezpieczony, możesz go zainstalować w magazynie głównego urzędu certyfikacji zaufanych certyfikatów).

5. Przejdź do okienka Akcje dla domyślnej witryny sieci Web. Kliknij pozycję Edytuj powiązania > lokacji. Dodaj protokół HTTPS jako typ, jeśli nie jest jeszcze obecny, z numerem portu 443 i przypisz certyfikat SSL utworzony w powyższym kroku.

6. Tworzenie usługi. Spowoduje to utworzenie katalogu wirtualnego w usługach IIS (z akcji po kompilacji określonej we właściwościach projektu) i skopiowanie plików DLL, svc i konfiguracji, zgodnie z wymaganiami, aby usługa była hostowana w sieci Web.

7. Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalog wirtualny (Kiedy), który został utworzony w poprzednim kroku, a następnie wybierz polecenie Konwertuj na aplikację.

8. Otwórz moduł uwierzytelniania w Menedżerze usług IIS dla tego katalogu wirtualnego i Włącz uwierzytelnianie systemu Windows.

9. Otwórz ustawienia zaawansowane uwierzytelniania systemu Windows dla tego katalogu wirtualnego i ustaw je na wymagane, ponieważ w przykładzie, odpowiednie ustawienie kiedy jest ustawione na zawsze.

10. Usługę można przetestować, uzyskując dostęp do adresu URL z okna przeglądarki. Jeśli chcesz uzyskać dostęp do tego adresu URL z wielu maszyn, upewnij się, że Zapora jest otwarta dla wszystkich przychodzących połączeń HTTP i HTTPS.

11. Otwórz plik konfiguracji klienta i podaj pełną nazwę komputera dla \<client>  -  \<endpoint> atrybutu-Address, zastępując ciąg \<full_machine_name> .

12. Uruchom klienta programu. Klient komunikuje się z usługą, ustanawiając bezpieczny kanał i używając rozszerzonej ochrony w ramach okładek.
