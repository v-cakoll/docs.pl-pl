---
title: Kolejność przetwarzania za pomocą zasad
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f99db44a636a5255990f734d34266b3b2e4a678b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="order-processing-with-policy"></a>Kolejność przetwarzania za pomocą zasad
Przykładowe kolejność przetwarzania zasad przedstawiono niektóre najważniejsze funkcje wprowadzone w systemie [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Nowy aparat reguł WF są następujące funkcje:  
  
-   Obsługa dotyczące przeciążania operatorów.  
  
-   Obsługa `new` operatora, dzięki czemu użytkownicy mogą tworzyć nowe obiekty i tablice z reguł WF.  
  
-   Obsługa metody rozszerzenia, aby interfejs w wywoływanie metod rozszerzeń z reguł WF użytkownika zgodny z styl kodowania C#.  
  
> [!NOTE]
>  W tym przykładzie wymaga, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] jest zainstalowany, aby skompilować i uruchomić. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest wymagany do otwierania plików projektu i rozwiązania.  
  
 W przykładzie pokazano `OrderProcessingPolicy` projektu w jest wprowadzana zamówienie klienta, składający się z Lista numerowana dostępne elementy i kod pocztowy. Kolejność jest przetworzone pomyślnie, jeśli obie pozycje są prawidłowe; w przeciwnym razie zasady tworzy obiekty błąd, wykorzystując przeciążone `+` operatora, a także metodę rozszerzenie wstępnie zdefiniowanych informują użytkownika o błędach.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat metody rozszerzenia, zobacz [C# w wersji 3.0 specyfikacji](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Próbka składa się z następujących projektów:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Jest biblioteki klas, który definiuje `OrderError` i `OrderErrorCollection` klasy. `OrderError` Jest tworzone wystąpienie, gdy wprowadzono nieprawidłowe dane wejściowe. Biblioteka zawiera także metodę rozszerzenia o `OrderErrorCollection` klasy, która wyświetla `ErrorText` właściwości na wszystkich `OrderError` obiekty w `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projekt jest aplikacją konsoli WF, która definiuje jedną `PolicyFromFile` działania. Działanie ma następujące reguły:  
  
    -   `invalidItemNum`  
  
         Ta reguła sprawdza, czy liczba elementów od 1 do 6 włącznie. Jeśli numer jest prawidłowego zakresu, reguła nie zadziała (inne niż drukowanie do konsoli). Jeśli numer nie jest od 1 do 6, `invalidItemNum` zasada wykonuje następujące czynności:  
  
        1.  Tworzy nowy `OrderError` obiektu, przekazanie jej numer wprowadzony i ustawia `ErrorText` i `CustomerName` właściwości obiektu.  
  
        2.  Tworzy `invalidItemNumErrorCollection` obiektu.  
  
        3.  Dodaje nowy `OrderError` wystąpienie do `invalidItemNumErrorCollection`.  
  
         Oznacza to obsługę `new` operatora, z którym można utworzyć wystąpienia obiektów wewnątrz reguły.  
  
    -   `invalidZip`  
  
         Ta reguła sprawdza, kod pocztowy zawiera 5 cyfr czy znajduje się w zakresie 99998 do 600. Jeśli kod pocztowy jest prawidłowego zakresu, reguła nie zadziała (inne niż drukowanie do konsoli). Jeśli długość kodu pocztowego jest mniejsza niż 5 lub kod pocztowy nie jest między 00600 i 99998, `invalidZip` zasada wykonuje następujące czynności:  
  
        1.  Tworzy `OrderError` obiektu, przekazanie jej wprowadzony, kod pocztowy i ustawia `ErrorText` i `CustomerName` właściwości obiektu.  
  
        2.  Tworzy `invalidZipCodeErrorCollection` obiektu.  
  
        3.  Dodaje nowy `OrderError` wystąpienie do nowo utworzonego `invalidZipCodeErrorCollection`.  
  
         Ta zasada ponownie przedstawiono obsługę `new` operatora, który służy do tworzenia wystąpienia obiektów wewnątrz reguły.  
  
    -   `displayErrors`  
  
         Ta reguła sprawdza, czy wystąpiły błędy dodane przez poprzednie dwie reguły w dwóch `OrderErrorCollection` obiektów `invalidItemNumErrorCollection` i `invalidIZipCodeErrorCollection`. Jeśli wystąpiły błędy (albo `invalidItemNumErrorCollection` lub `invalidZipCodeErrorCollection` nie jest `null`), reguła wykonuje następujące czynności:  
  
        1.  Wywołuje przeciążone `+` operatora, aby skopiować zawartość `invalidItemNumErrorCollection` i `invalidZipCodeErrorCollection` do `invalidOrdersCollection``OrderErrorCollection` wystąpienia.  
  
        2.  Wywołania `PrintOrderErrors` — metoda rozszerzenia na `invalidOrdersCollection` i wyprowadza `ErrorText` właściwości na wszystkich `orderError` obiekty w `invalidOrdersCollection`.  
  
 Przeciążony operator `+` na `OrderErrorCollection` jest zdefiniowany w `OrderErrorCollection` klasy w `OrderErrorLibrary` projektu. Trwa dwa `OrderErrorCollection` obiekty i łączy je do jednej `OrderErrorCollection` obiektu.  
  
 `PrintOrderErrors` — Metoda rozszerzenia jest też definiowany w `OrderErrorLibrary` projektu. Metody rozszerzenia są nowe C# funkcję, która umożliwia programistom dodawanie nowych metod do publicznego kontraktu istniejącego typu CLR, bez konieczności pochodną klasy lub skompiluj ponownie oryginalnego typu.  
  
 Po uruchomieniu próbki monit wprowadź nazwę, numer elementu zakupu i kod pocztowy. Te informacje jest następnie weryfikowany przez reguły zdefiniowane w działaniu zasad. Oto przykładowe dane wyjściowe z programu.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Otwórz plik projektu OrderProcessingPolicy.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Istnieją dwa różne projekty w rozwiązaniu: `OrderErrorLibrary` i `OrderProcessingPolicy`. `OrderProcessingPolicy` Projekt używa klasy i metody zdefiniowane w `OrderErrorLibrary`.  
  
3.  Tworzenie wszystkich projektów.  
  
4.  Kliknij przycisk **Uruchom**.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`