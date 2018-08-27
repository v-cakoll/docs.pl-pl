---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: ea4dd376cfeda6a9f05e45940fac91abd2d4f22e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925370"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zdarzeniach
Jeśli piszesz klasy z niektórych operacji, które może spowodować naliczenie zauważalnego opóźnienia, należy wziąć pod uwagę nadając mu funkcje asynchroniczne z zastosowaniem [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Asynchroniczny wzorzec oparty na zdarzeniach udostępnia standardowy sposób pakietu klasę, która ma funkcje asynchroniczne. Jeśli implementowane za pomocą klas pomocniczych, takich jak <xref:System.ComponentModel.AsyncOperationManager>, klasa będzie działać poprawnie w dowolnym modelu aplikacji, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplikacji konsoli i aplikacji Windows Forms.  
  
 Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Dla prostych operacji asynchronicznych, może się okazać <xref:System.ComponentModel.BackgroundWorker> odpowiedniego składnika. Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker>, zobacz [porady: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Na poniższej liście opisano funkcje oparte na zdarzeniach wzorca asynchronicznego omówione w tym temacie.  
  
-   Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach  
  
-   Nazwy metod asynchronicznych  
  
-   Opcjonalnie obsługują anulowania  
  
-   Opcjonalnie obsługiwać Właściwość IsBusy  
  
-   Opcjonalnie zapewnia obsługę raportowania postępu  
  
-   Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe  
  
-   Obsługa się i parametry Ref w metodach  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Możliwości implementacja wzorca asynchronicznego opartego na zdarzeniach  
 Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach — gdy:  
  
-   Nie ma potrzeby klientów klasy <xref:System.Threading.WaitHandle> i <xref:System.IAsyncResult> obiektów dostępnych dla operacji asynchronicznych, co oznacza, że sondowania i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> musi być tworzone przez klienta.  
  
-   Chcesz, aby operacje asynchroniczne, które mają być zarządzane przez klienta za pomocą dobrze znanych delegat wydarzenia/modelu.  
  
 Wszelkie działania jest kandydatem do implementacji asynchronicznego, ale należy rozważyć te spodziewasz się ponieść długie opóźnienia. Dostępne są szczególnie odpowiednie operacje, w których klienci wywołania metody oraz powiadomienie po zakończeniu, bez potrzeby interwencji dalsze. Odpowiednie są także działań, które w sposób ciągły, uruchamianie, okresowe powiadamiania klientów postępu, przyrostowe wyników lub zmiany stanu.  
  
 Aby uzyskać więcej informacji o podjęcie decyzji na potrzeby obsługi wzorca asynchronicznego opartego na zdarzeniach, zobacz [podejmowania decyzji podczas implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Nazwy metod asynchronicznych  
 Dla każdej metody synchronicznej *MethodName* dla którego chcesz zapewnić odpowiednika asynchronicznego:  
  
 Zdefiniuj *MethodName *** Async** metoda który:  
  
-   Zwraca `void`.  
  
-   Przyjmuje te same parametry jako *MethodName* metody.  
  
-   Akceptuje wiele wywołań.  
  
 Opcjonalnie zdefiniowanie *MethodName *** Async** przeciążenia, taka sama jak * MethodName ***Async**, ale o dodatkowy parametr zwracającej obiekt o nazwie `userState`. To zrobić, jeśli masz przygotowany do zarządzania wielu równoczesnych wywołań metodę, w którym to przypadku `userState` wartości, które zostaną dostarczone do wszystkich procedur obsługi zdarzeń w celu odróżnienia wywołania metody. Możesz również w tym celu po prostu jako miejsce do przechowywania stanu użytkownika na nowsze pobierania.  
  
 Dla każdego oddzielnego *MethodName *** Async** sygnatury metody:  
  
1.  W tej samej klasy jako metodę, należy zdefiniować następujące zdarzenie:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Zdefiniuj następujące delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs>. Te prawdopodobnie zostanie zdefiniowany, poza samej klasy, ale w tej samej przestrzeni nazw.  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   Upewnij się, że *MethodName *** CompletedEventArgs** klasa udostępnia jej elementów członkowskich jako właściwości tylko do odczytu, a nie pola jako pola Zapobiegaj powiązaniu danych.  
  
    -   Nie definiują <xref:System.ComponentModel.AsyncCompletedEventArgs>-pochodnych klas do metody, które nie dawać wyników. Po prostu użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> sam.  
  
        > [!NOTE]
        >  Doskonale dopuszczalne jest, gdy jest to możliwe i właściwe ponownie użyć delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów. W tym przypadku nazewnictwo nie będzie jako zgodne z nazwy metody od danego delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie będzie powiązany do pojedynczej metody.  
  
## <a name="optionally-support-cancellation"></a>Opcjonalnie obsługują anulowania  
 Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, powinny zostać ujawnione anulowania do klienta, zgodnie z poniższym opisem. Należy zwrócić uwagę na to, że istnieją dwa punkty decyzyjne, które trzeba osiągnąć przed zdefiniowaniem dział pomocy technicznej Twojej anulowania:  
  
-   Klasy, w tym przyszłych przewidywanego dodatki, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?  
  
-   Czy operacje asynchroniczne, obsługujące wiele oczekujących operacji obsługi anulowania? Oznacza to, że jest *MethodName *** Async** take metoda `userState` parametru i zezwala na wiele wywołań przed oczekiwania na zakończenie?  
  
 Użyj odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, jakie powinny być podpis dla wybranej metody anulowania.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Wiele jednoczesnych operacji obsługiwane|Tylko jedną operację naraz|  
|------|------------------------------------------------|----------------------------------|  
|Jednej operacji asynchronicznych w całej klasy|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Wiele operacji asynchronicznych w klasie|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Wiele jednoczesnych operacji obsługiwane|Tylko jedną operację naraz|  
|------|------------------------------------------------|----------------------------------|  
|Jednej operacji asynchronicznych w całej klasy|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Wiele operacji asynchronicznych w klasie|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Jeśli zdefiniujesz `CancelAsync(object userState)` metody klientów należy zachować ostrożność, wybierając ich wartości stanu, aby były one zdolne do rozróżniania wszystkich metod asynchronicznych, wywołana dla obiektu, a nie tylko między wszystkie wywołania jednej metody asynchronicznej.  
  
 Decyzja o nazwę wersji pojedynczego asynchronicznych operacji *MethodName *** AsyncCancel** opiera się na możliwości łatwiej odnaleźć metody w środowisku projektowania, takie jak technologia IntelliSense programu Visual Studio. Grupuje pokrewne elementy członkowskie, a odróżnia je od innych użytkowników, które mają one nic wspólnego z funkcji asynchronicznych. Jeśli spodziewasz się, że mogą istnieć dodatkowe dodany operacji asynchronicznych w kolejnych wersjach to lepiej zdefiniować `CancelAsync`.  
  
 Nie zostaną zdefiniowane z powyższej tabeli na wiele sposobów w tej samej klasy. Który nie ma sensu lub go będzie zbliżyć do siebie te interfejsu klasy za pomocą rozprzestrzenianie metody.  
  
 Tych metodach zwykle zwróci natychmiast i operację może lub nie może w rzeczywistości anulować. W procedurze obsługi zdarzeń dla *MethodName *** Ukończono** zdarzenia *MethodName *** CompletedEventArgs** obiekt zawiera `Cancelled` pola, które klienci mogą używać, aby określić, czy nastąpiło anulowanie.  
  
 Przestrzeganie semantyki anulowania opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Opcjonalnie obsługiwać Właściwość IsBusy  
 Jeśli klasa nie obsługuje wielu równoczesnych wywołań, należy rozważyć uwidocznienie `IsBusy` właściwości. Dzięki temu deweloperzy mogą określić, czy *MethodName *** Async** metodą jest uruchomienie bez przechwytywanie wyjątku z *MethodName *** Async** metody.  
  
 Przestrzeganie `IsBusy` semantyki opisanego w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Opcjonalnie zapewnia obsługę raportowania postępu  
 Jest często pożądane dla operacji asynchronicznej do raportowania postępu podczas jego działania. Asynchroniczny wzorzec oparty na zdarzeniach przedstawiono wskazówki, aby to zrobić.  
  
-   Opcjonalnie zdefiniowanie zdarzenia wygenerowane przez operację asynchroniczną i wywoływane dla odpowiedniego wątku. <xref:System.ComponentModel.ProgressChangedEventArgs> Obiektu niesie ze sobą wskaźnik postępu wartości całkowitych, który powinien należeć do zakresu od 0 do 100.  
  
-   Nazwa tego zdarzenia w następujący sposób:  
  
    -   `ProgressChanged` Jeśli klasa ma wiele operacji asynchronicznych (lub oczekuje się, że powiększona i obejmie wiele operacji asynchronicznych w przyszłych wersjach)  
  
    -   *MethodName *** ProgressChanged** Jeśli klasa ma jedną operację asynchroniczną.  
  
     Ten wybór nazewnictwa równoleżnikami zgłaszający metody anulowania, zgodnie z opisem w sekcji opcjonalnie anulowania obsługi.  
  
 Skorzystaj z tego zdarzenia <xref:System.ComponentModel.ProgressChangedEventHandler> podpis delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy. Alternatywnie, jeśli można podać wskaźnik postępu bardziej specyficznego dla domeny (w przypadku wystąpienia, Bajty odczytane i całkowita liczba bajtów dla operacji pobierania), następnie należy zdefiniować klasę pochodną z <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Należy pamiętać, że istnieje tylko jeden `ProgressChanged` lub *MethodName *** ProgressChanged** zdarzeń dla tej klasy, niezależnie od liczby metod asynchronicznych, które obsługuje. Klienci powinni używać `userState` obiekt, który jest przekazywany do *MethodName *** Async** metody w celu rozróżnienia aktualizacji w toku na wiele jednoczesnych operacji.  
  
 Mogą wystąpić sytuacje, w których wiele operacji obsługi postępu, a każda zwraca inny wskaźnik postępu. W tym przypadku jeden `ProgressChanged` zdarzeń nie jest odpowiednie, a może rozważyć, obsługa wielu `ProgressChanged` zdarzenia. W tym przypadku użyj wzorzec nazewnictwa *MethodName *** ProgressChanged** dla każdego *MethodName *** Async** metody.  
  
 Przestrzeganie semantykę raportowania postępu opisane [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Opcjonalnie zapewnia obsługę zwracania wyników przyrostowe  
 Czasami operacji asynchronicznej może zwrócić wyniki przyrostową przed ukończeniem. Istnieje kilka opcji, które mogą służyć do obsługi tego scenariusza. Oto niektóre przykłady.  
  
### <a name="single-operation-class"></a>Jednym operation — klasa  
 Jeśli klasa obsługuje tylko jedną operację asynchroniczną, a tej operacji jest w stanie zwracają przyrostowe, następnie:  
  
-   Rozszerzanie <xref:System.ComponentModel.ProgressChangedEventArgs> wpisz do przenoszenia danych przyrostowych wyników, a następnie zdefiniuj *MethodName *** ProgressChanged** zdarzeń za pomocą rozszerzenia danych.  
  
-   Wywoływanie to *MethodName *** ProgressChanged** zdarzenie, kiedy ma wynik przyrostowe do raportu.  
  
 To rozwiązanie odnosi się do klasy pojedynczej asynchronicznych operacji ponieważ nie istnieje żaden problem za pomocą tego samego zdarzenia występujące w celu zwracania wyników przyrostowych na "wszystkie operacje", jako *MethodName *** ProgressChanged** jest zdarzenie.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Klasa wielu operacji z jednorodnych wyniki przyrostowe  
 W takim przypadku klasa obsługuje wiele metod asynchronicznych, każdy może zwracanie wyników przyrostowe i przyrostowe wyniki te wszystkie mają ten sam typ danych.  
  
 Postępuj zgodnie z modelem opisane powyżej, aby klasy pojedynczej operacji, taka sama <xref:System.EventArgs> struktury będzie działać w przypadku wszystkich wyników przyrostowe. Zdefiniuj `ProgressChanged` zdarzeń zamiast *MethodName *** ProgressChanged** zdarzenie, ponieważ dotyczy on wiele metod asynchronicznych.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Klasa wielu operacji z heterogenicznych wyniki przyrostowe  
 Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwraca innego typu danych, należy:  
  
-   Oddziel wynik Twojego przyrostowe raportów z raportowania postępu.  
  
-   Zdefiniuj oddzielnego *MethodName *** ProgressChanged** zdarzeń z odpowiednich <xref:System.EventArgs> dla poszczególnych metod asynchronicznych do obsługi danych przyrostowych wyniku tej metody.  
  
 Wywoływanie tej obsługi zdarzeń w odpowiednich wątku, zgodnie z opisem w [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Obsługa się i parametry Ref w metodach  
 Mimo że korzystanie z `out` i `ref` jest, ogólnie rzecz biorąc, zalecane w programie .NET Framework, poniżej przedstawiono reguły, które należy wykonać podczas są obecne:  
  
 Podana metoda synchroniczna *MethodName*:  
  
-   `out` Parametry *MethodName* nie powinna być częścią *MethodName ***Async**. Zamiast tego powinien być częścią *MethodName *** CompletedEventArgs**  z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie nazwy).  
  
-   `ref` Parametry *MethodName* powinny się wyświetlać jako część *MethodName ***Async**oraz jako część *MethodName *** CompletedEventArgs**  z taką samą nazwę jak parametr równoważne w *MethodName* (chyba że istnieje bardziej odpowiednie nazwy).  
  
 Na przykład biorąc pod uwagę:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Metoda asynchronicznego i jego <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy będzie wyglądać następująco:  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
