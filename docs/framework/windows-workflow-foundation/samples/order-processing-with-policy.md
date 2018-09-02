---
title: Przetwarzanie kolejności za pomocą zasad
ms.date: 03/30/2017
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
ms.openlocfilehash: b927d8e7090f96b22c0510f9651070ab999c91be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398373"
---
# <a name="order-processing-with-policy"></a>Przetwarzanie kolejności za pomocą zasad
W przykładzie kolejność przetwarzania zasad pokazano niektóre z kluczowych funkcji wprowadzonych w [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] Windows Workflow Foundation (WF). Nowy aparat reguł WF są następujące funkcje:  
  
-   Obsługa przeciążenia operatora.  
  
-   Obsługa `new` operatora, dzięki czemu użytkownicy mogą tworzyć nowe obiekty i tablice z reguł WF.  
  
-   Pomoc techniczna dla metody rozszerzenia ułatwić podczas wywoływania metody rozszerzenia reguł WF zgodny z kodowania stylów języka C#.  
  
> [!NOTE]
>  W tym przykładzie wymaga, aby [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] jest zainstalowany, aby skompilować i uruchomić. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jest wymagany do otwierania plików projektu i rozwiązania.  
  
 W przykładzie pokazano `OrderProcessingPolicy` projektu w jest wprowadzana zamówienia klienta, który składa się z listy numerowanej dostępne elementy i kod pocztowy,. Kolejność jest przetwarzany pomyślnie, jeśli obie wpisy są poprawne; w przeciwnym razie zasady tworzy obiekty błąd, wykorzystując przeciążony `+` operatora i metoda wstępnie zdefiniowanych rozszerzeń informować użytkownika błędy.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących metod rozszerzających, zobacz [C# w wersji 3.0 specyfikacji](https://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Przykład składa się z następujących projektów:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` Jest bibliotekę klas, który definiuje `OrderError` i `OrderErrorCollection` klasy. `OrderError` Tworzone jest wystąpienie, gdy wprowadzono nieprawidłowe dane wejściowe. Biblioteka zawiera także metodę rozszerzającą o `OrderErrorCollection` klasę, która generuje `ErrorText` właściwości na wszystkich `OrderError` obiekty w `OrderErrorCollection`.  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` Projekt to aplikacja konsoli WF, która definiuje pojedyncze `PolicyFromFile` działania. Działanie ma następujące reguły:  
  
    -   `invalidItemNum`  
  
         Ta reguła sprawdza numer od 1 do 6 (włącznie). Jeśli numer jest prawidłowego zakresu, reguła nie działa (inne niż drukowanie do konsoli). Jeśli liczba elementów nie jest od 1 do 6, `invalidItemNum` reguły wykonuje następujące czynności:  
  
        1.  Tworzy nową `OrderError` obiekt przekazywanie jej przez numer wprowadzony i ustawia `ErrorText` i `CustomerName` właściwości w obiekcie.  
  
        2.  Tworzy `invalidItemNumErrorCollection` obiektu.  
  
        3.  Dodaje nowo utworzony `OrderError` wystąpienia do `invalidItemNumErrorCollection`.  
  
         W tym przykładzie pokazano obsługę `new` operatora, za pomocą którego można utworzyć wystąpienie obiektów wewnątrz reguły.  
  
    -   `invalidZip`  
  
         Ta reguła sprawdza, czy kod pocztowy z 5 cyfr, a znajduje się w zakresie 600, 99998. Jeśli kod pocztowy jest prawidłowego zakresu, reguła nie działa (inne niż drukowanie do konsoli). Jeśli długość kod pocztowy jest mniejsza niż 5 lub kod pocztowy nie jest między 00600 i 99998, `invalidZip` reguły wykonuje następujące czynności:  
  
        1.  Tworzy `OrderError` obiektu, podając mu kod pocztowy wprowadzona i ustawia `ErrorText` i `CustomerName` właściwości w obiekcie.  
  
        2.  Tworzy `invalidZipCodeErrorCollection` obiektu.  
  
        3.  Dodaje nowo utworzony `OrderError` wystąpienie do nowo utworzony `invalidZipCodeErrorCollection`.  
  
         Ta zasada ponownie Pokazuje obsługę `new` operatora, który służy do tworzenia wystąpień obiektów wewnątrz reguły.  
  
    -   `displayErrors`  
  
         Ta reguła sprawdza, czy wystąpiły błędy dodane przez poprzednie dwie reguły na obu `OrderErrorCollection` obiektów `invalidItemNumErrorCollection` i `invalidIZipCodeErrorCollection`. Jeśli wystąpiły błędy (albo `invalidItemNumErrorCollection` lub `invalidZipCodeErrorCollection` nie `null`), reguła wykonuje następujące czynności:  
  
        1.  Wywołania przeciążonych `+` operatora, aby skopiować zawartość `invalidItemNumErrorCollection` i `invalidZipCodeErrorCollection` do `invalidOrdersCollection``OrderErrorCollection` wystąpienia.  
  
        2.  Wywołania `PrintOrderErrors` metody rozszerzenia `invalidOrdersCollection` i generuje `ErrorText` właściwości na wszystkich `orderError` obiekty w `invalidOrdersCollection`.  
  
 Przeciążony operator `+` na `OrderErrorCollection` jest zdefiniowany w `OrderErrorCollection` klasy w `OrderErrorLibrary` projektu. Trwa dwa `OrderErrorCollection` obiektów i łączy je w jedną `OrderErrorCollection` obiektu.  
  
 `PrintOrderErrors` — Metoda rozszerzenia jest także zdefiniowana w `OrderErrorLibrary` projektu. Metody rozszerzające są nową C# funkcję, która umożliwia deweloperom Dodawanie nowych metod publicznych umowy istniejącego typu CLR, bez konieczności dziedziczyć po nim klasę lub ponownie skompilować oryginalnego typu.  
  
 Po uruchomieniu przykładu wyświetleniu monitu wprowadź nazwę, numer pozycji do zakupu i kod pocztowy. Informacja ta jest następnie weryfikowany przez od reguł zdefiniowanych w działanie zasad. Poniżej przedstawiono przykładowe dane wyjściowe z programu.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Otwórz plik projektu OrderProcessingPolicy.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Istnieją dwa różne projekty w rozwiązaniu: `OrderErrorLibrary` i `OrderProcessingPolicy`. `OrderProcessingPolicy` Projekt korzysta z klasy i metody zdefiniowane w `OrderErrorLibrary`.  
  
3.  Kompiluj wszystkie projekty.  
  
4.  Kliknij przycisk **Uruchom**.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`