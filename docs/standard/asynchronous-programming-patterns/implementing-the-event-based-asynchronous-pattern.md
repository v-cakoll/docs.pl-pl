---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c503b89c63d976fe6304291aa1157765fa5c6f7
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zdarzeniach
Podczas pisania klasy z niektórych operacji, które może pociągnąć za sobą zauważalnego opóźnienia, należy wziąć pod uwagę nadanie mu funkcji asynchroniczności zaimplementowanie [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Asynchroniczny wzorzec oparty na zdarzeniach umożliwia standardowych pakietu klasy, która ma funkcje asynchroniczne. Zaimplementowany przy użyciu Pomocnika klas takich jak <xref:System.ComponentModel.AsyncOperationManager>, klasy będzie działać poprawnie w dowolnej aplikacji modelu, w tym [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplikacje konsoli i aplikacji formularzy systemu Windows.  
  
 Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [porady: implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Proste operacje asynchroniczne, może znaleźć <xref:System.ComponentModel.BackgroundWorker> odpowiedniego składnika. Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker>, zobacz [porady: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Poniższa lista zawiera opis funkcji oparty na zdarzeniach wzorca asynchronicznego omówione w tym temacie.  
  
-   Możliwości w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach  
  
-   Nazwy metod asynchronicznych  
  
-   Opcjonalnie obsługiwać anulowania  
  
-   Opcjonalnie obsługiwać Właściwość IsBusy  
  
-   Opcjonalnie zapewniają obsługę raportowania postępu  
  
-   Opcjonalnie zapewniają obsługę zwracania wyników przyrostowe  
  
-   Obsługa Out i Ref parametrów metod  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Możliwości w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach  
 Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach po:  
  
-   Nie ma potrzeby klientów klasy <xref:System.Threading.WaitHandle> i <xref:System.IAsyncResult> obiekty dostępne dla operacji asynchronicznych, co oznacza, że sondowania i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> musi być tworzone przez klienta.  
  
-   Chcesz, aby operacje asynchroniczne, które mają być zarządzane przez klienta z modelem znanych zdarzeń lub obiekt delegowany.  
  
 Żadnej operacji jest kandydatem do asynchronicznego implementacji, ale należy rozważyć te może pociągnąć za sobą długie opóźnienia. Szczególnie przydatne są operacje, w których klienci wywołania metody i są powiadamiani o po zakończeniu, bez potrzeby interwencji dodatkowe. Odpowiednie są również działań, które w sposób ciągły, uruchom okresowo powiadamiania klientów postępu, przyrostowe wyników lub zmiany stanu.  
  
 Aby uzyskać więcej informacji o podjęcie decyzji o obsługującego wzorzec asynchroniczny oparty na zdarzeniach, zobacz [przy wyborze, gdy do implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Nazwy metod asynchronicznych  
 Dla każdej z metod synchronicznych *MethodName* dla którego chcesz podać asynchroniczne odpowiednikiem:  
  
 Zdefiniuj *MethodName *** Async** metody który:  
  
-   Zwraca `void`.  
  
-   Trwa takich samych parametrach co *MethodName* metody.  
  
-   Akceptuje wiele wywołań.  
  
 Opcjonalnie zdefiniować *MethodName *** Async** przeciążenia taki sam jak * MethodName ***Async**, wywołuje się, ale bez dodatkowy parametr zwracającej obiekt `userState`. Jeśli jest przygotowane do zarządzania wielu współbieżnych wywołań metodę, w którym to przypadku `userState` wartości będą dostarczane do wszystkich procedur obsługi zdarzeń w celu odróżnienia wywołania metody. Można też to zrobić po prostu jako miejsce do przechowywania stanu użytkownika późniejszym pobierania.  
  
 Dla każdej szczegółowej *MethodName *** Async** podpis metody:  
  
1.  W tej samej klasie metodą, należy zdefiniować następujące zdarzenie:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Zdefiniuj następujące delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs>. Te będą prawdopodobnie zdefiniowania poza samej klasy, ale w tej samej przestrzeni nazw.  
  
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
  
    -   Upewnij się, że *MethodName *** CompletedEventArgs** klasy udostępnia jej elementów członkowskich jako właściwości tylko do odczytu i nie pola jako pola Zapobiegaj wiązania z danymi.  
  
    -   Nie definiują <xref:System.ComponentModel.AsyncCompletedEventArgs>-pochodnych klas do metody, które nie dostarczyło wyników. Po prostu użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> samej siebie.  
  
        > [!NOTE]
        >  Doskonale dopuszczalne jest, gdy to możliwe i należy używać ponownie delegata i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów. W takim przypadku nazewnictwo nie będzie jako zgodne z nazwą metody od danego obiektu delegowanego i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie będą powiązane do pojedynczej metody.  
  
## <a name="optionally-support-cancellation"></a>Opcjonalnie obsługiwać anulowania  
 Jeśli klasa będzie obsługiwał anulowanie operacji asynchronicznych, powinny zostać ujawnione anulowania do klienta, zgodnie z poniższym opisem. Należy pamiętać, że istnieją dwa punkty decyzyjne, które trzeba osiągnąć przed zdefiniowaniem zainteresowanie anulowania:  
  
-   Klasy, w tym przyszłych przewidywanego dodatków, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?  
  
-   Można operacje asynchroniczne, które obsługują wiele oczekujących operacji anulowania obsługi? Oznacza to, że jest *MethodName *** Async** Wykonaj metodę `userState` parametru i jest możliwe wielu wywołań przed oczekiwania na zakończenie?  
  
 Użyj odpowiedzi na te pytania dwóch w poniższej tabeli, aby określić, jakie powinny być sygnatury dla metody anulowania.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Wiele równoczesnych operacji obsługiwane|Tylko jedną operację naraz|  
|------|------------------------------------------------|----------------------------------|  
|Jednej operacji asynchronicznej w całej klasy|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Wiele operacji asynchronicznych w klasie|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Wiele równoczesnych operacji obsługiwane|Tylko jedną operację naraz|  
|------|------------------------------------------------|----------------------------------|  
|Jednej operacji asynchronicznej w całej klasy|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Wiele operacji asynchronicznych w klasie|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 W przypadku definiowania `CancelAsync(object userState)` metody klientów należy zachować ostrożność, wybierając wartości stanu, aby pozwala na rozróżniania wśród wszystkich metod asynchronicznych wywołana dla obiektu, a nie tylko od wszystkich wywołań jednej metody asynchronicznej.  
  
 Decyzja o nazwę wersji jednym asynchroniczne operacje *MethodName *** AsyncCancel** jest oparta na było łatwiej odnaleźć metody w środowisku projektowania, takie jak IntelliSense programu Visual Studio. Grupuje pokrewne elementy członkowskie, a odróżnia je od innych elementów członkowskich, które nie mają nic wspólnego z funkcji asynchronicznych. Jeśli przypuszczasz, że mogą istnieć dodatkowe operacje asynchroniczne dodane w kolejnych wersjach, lepiej zdefiniować `CancelAsync`.  
  
 Wiele metod z powyższej tabeli nie zostaną zdefiniowane w tej samej klasy. Że nie ma sensu lub będzie zajmowały interfejsu klasy z mnożenie metody.  
  
 Te metody zwykle zwróci natychmiast i operacji może lub nie może faktycznie anulowania. W obsłudze zdarzeń dla *MethodName *** Ukończono** zdarzeń, *MethodName *** CompletedEventArgs** obiekt zawiera `Cancelled` pola, którego klienci mogą używać, aby określić, czy podczas anulowania.  
  
 Przestrzegać semantyki anulowania opisanego w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Opcjonalnie obsługiwać Właściwość IsBusy  
 Jeśli klasa nie obsługuje wiele równoczesnych wywołań, należy wziąć pod uwagę udostępnianie `IsBusy` właściwości. Dzięki temu deweloperzy mogą określić, czy *MethodName *** Async** metody działa bez przechwytywanie wyjątku z *MethodName *** Async** — metoda.  
  
 Przestrzegać `IsBusy` semantyki opisanego w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Opcjonalnie zapewniają obsługę raportowania postępu  
 Jest często pożądane asynchronicznej operacji postępu raportu podczas jego działania. Asynchroniczny wzorzec oparty na zdarzeniach zawiera wytyczne w ten sposób.  
  
-   Opcjonalnie zdefiniować zdarzenia wygenerowane przez operację asynchroniczną i wywołany w wątku odpowiednie. <xref:System.ComponentModel.ProgressChangedEventArgs> Obiektu prowadzi wskaźnik postępu wyliczaną, który może należeć do zakresu od 0 do 100.  
  
-   Nazwa tego zdarzenia w następujący sposób:  
  
    -   `ProgressChanged`Jeśli klasa ma wiele operacji asynchronicznych (lub jest oczekiwana Powiększ, aby dołączyć wielu operacji asynchronicznych w przyszłych wersjach);  
  
    -   *MethodName *** ProgressChanged** Jeśli klasa ma jednej operacji asynchronicznej.  
  
     Ten wybór nazewnictwa równoleżnikami zgłaszającego dla metody anulowania, zgodnie z opisem w sekcji opcjonalnie anulowania obsługi.  
  
 To zdarzenie należy używać <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy. Alternatywnie, jeśli wskaźnik postępu bardziej specyficznego dla domeny można podać (w przypadku wystąpienia odczytanych bajtów i łączna liczba bajtów dla operacji pobierania), następnie należy zdefiniować klasy pochodnej z <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Należy pamiętać, że istnieje tylko jeden `ProgressChanged` lub *MethodName *** ProgressChanged** zdarzenia dla klasy, niezależnie od liczby obsługiwanych metod asynchronicznych. Klienci powinni używać `userState` obiekt, który jest przekazywany do *MethodName *** Async** metody do odróżnienia postępu aktualizacji na wiele równoczesnych operacji.  
  
 Mogą wystąpić sytuacje, w których wiele operacji obsługuje postępu i zwraca każdego innego wskaźnika postępu. W tym przypadku jednej `ProgressChanged` zdarzeń nie jest odpowiedni i można rozważyć obsługi wielu `ProgressChanged` zdarzenia. W takim przypadku należy użyć wzorzec nazewnictwa *MethodName *** ProgressChanged** dla każdego *MethodName *** Async** metody.  
  
 Przestrzegać semantykę raportowania postępu opisane [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Opcjonalnie zapewniają obsługę zwracania wyników przyrostowe  
 Czasami operację asynchroniczną może zwrócić wyniki przyrostowe przed ukończeniem. Istnieją różne opcje, które mogą służyć do obsługi tego scenariusza. Oto niektóre przykłady.  
  
### <a name="single-operation-class"></a>Klasy pojedynczej operacji  
 Jeśli klasa obsługuje tylko jednej operacji asynchronicznych i tej operacji może zwrócić wyniki przyrostowych, następnie:  
  
-   Rozszerzanie <xref:System.ComponentModel.ProgressChangedEventArgs> typu przenoszenia danych przyrostowych wyników i zdefiniuj *MethodName *** ProgressChanged** zdarzenie z rozszerzenia danych.  
  
-   Zgłoś to *MethodName *** ProgressChanged** zdarzenie, gdy istnieje przyrostowe wynik do raportu.  
  
 To rozwiązanie dotyczy w szczególności klasy pojedynczej asynchronicznej operacji ponieważ nie ma problemów z tego samego zdarzenia występujące zwraca wyniki przyrostowe na "wszystkie operacje", jako *MethodName *** ProgressChanged** jest zdarzenie.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Klasa wielu operacji jednorodnych wyniki przyrostowe  
 W takim przypadku klasa obsługuje wiele metod asynchronicznych, każdy może zwracania wyników przyrostowych i przyrostowych wszystkie wyniki mają ten sam typ danych.  
  
 Postępuj zgodnie z modelem opisane powyżej, aby klasy pojedynczej operacji, jako takie same <xref:System.EventArgs> struktury będzie działać w przypadku wszystkich wyników przyrostowe. Zdefiniuj `ProgressChanged` zdarzeń zamiast *MethodName *** ProgressChanged** zdarzenie, ponieważ dotyczy on wiele metod asynchronicznych.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Klasa wielu operacji heterogenicznych wyniki przyrostowe  
 Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwracanie różnych typów danych, wykonaj następujące czynności:  
  
-   Oddzielne przyrostowe wyników raportowania raportowania postępu.  
  
-   Zdefiniuj oddzielnej *MethodName *** ProgressChanged** zdarzeń z odpowiednich <xref:System.EventArgs> dla każdej metody asynchronicznej do obsługi danych przyrostowych wyniku tej metody.  
  
 Wywołania programu obsługi zdarzeń w odpowiednich wątku, zgodnie z opisem w [najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Obsługa Out i Ref parametrów metod  
 Mimo że korzystanie z `out` i `ref` , ogólnie rzecz biorąc, zalecane w programie .NET Framework, poniżej przedstawiono zasady, zgodnie z którą są obecne:  
  
 Podana metoda synchroniczna *MethodName*:  
  
-   `out`Parametry *MethodName* nie powinna być częścią *MethodName ***Async**. Zamiast tego powinna być częścią *MethodName *** CompletedEventArgs**  o takiej samej nazwie jak jej parametr odpowiadającej *MethodName* (chyba że jest bardziej odpowiednia nazwa).  
  
-   `ref`Parametry *MethodName* powinny się wyświetlać jako część *MethodName ***Async**i w ramach *MethodName *** CompletedEventArgs**  o takiej samej nazwie jak jej parametr odpowiadającej *MethodName* (chyba że jest bardziej odpowiednia nazwa).  
  
 Przykładowo podana:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Metodę asynchroniczną i jego <xref:System.ComponentModel.AsyncCompletedEventArgs> klasy będzie wyglądać następująco:  
  
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
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
