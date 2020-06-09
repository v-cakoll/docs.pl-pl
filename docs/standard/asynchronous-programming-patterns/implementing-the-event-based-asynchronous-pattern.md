---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
description: Dowiedz się, jak zaimplementować wzorzec asynchroniczny oparty na zdarzeniach (EAP) w programie .NET. Protokół EAP jest standardowym sposobem spakowania klasy, która ma funkcje asynchroniczne.
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
ms.openlocfilehash: 9ffb2e2f426e2d2d97998a89a3e8d306de4f29ca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583664"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zdarzeniach

W przypadku pisania klasy z niektórymi operacjami, które mogą mieć zauważalne opóźnienia, należy rozważyć udzielenie funkcji asynchronicznych przez implementację [asynchronicznego wzorca opartego na zdarzeniach](event-based-asynchronous-pattern-overview.md).

Wzorzec asynchroniczny oparty na zdarzeniach zapewnia ustandaryzowany sposób spakowania klasy, która ma funkcje asynchroniczne. Jeśli zaimplementowano klasy pomocnika, takie jak <xref:System.ComponentModel.AsyncOperationManager> , Klasa będzie działała prawidłowo w ramach dowolnego modelu aplikacji, w tym ASP.NET, aplikacji konsolowych i aplikacji Windows Forms.

Aby zapoznać się z przykładem, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [How to: Implementuj składnik, który obsługuje wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md).

W przypadku prostych operacji asynchronicznych można znaleźć <xref:System.ComponentModel.BackgroundWorker> odpowiedni składnik. Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.BackgroundWorker> , zobacz [jak: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md).

Na poniższej liście opisano funkcje wzorca asynchronicznego opartego na zdarzeniach omówione w tym temacie.

- Możliwości implementacji wzorca asynchronicznego opartego na zdarzeniach

- Nazewnictwo metod asynchronicznych

- Opcjonalna obsługa anulowania

- Opcjonalnie można obsługiwać Właściwość IsBusy

- Opcjonalnie zapewniaj obsługę raportowania postępu

- Opcjonalnie zapewnić obsługę zwracania wyników przyrostowych

- Obsługa parametrów out i ref w metodach

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Możliwości implementacji wzorca asynchronicznego opartego na zdarzeniach

Rozważ zaimplementowanie wzorca asynchronicznego opartego na zdarzeniach, gdy:

- Klienci klasy nie potrzebują <xref:System.Threading.WaitHandle> i są <xref:System.IAsyncResult> obiektami dostępnymi dla operacji asynchronicznych, co oznacza, że sondowanie i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> wymagane jest skompilowanie przez klienta.

- Chcesz, aby operacje asynchroniczne były zarządzane przez klienta z modelem znanego zdarzenia/delegata.

Każda operacja jest kandydatem do implementacji asynchronicznej, ale powinny być brane pod uwagę długie opóźnienia. Szczególnie odpowiednie są operacje, w których klienci wywołujący metodę i są powiadamiani o zakończeniu, bez konieczności dalszej interwencji. Odpowiednie są również operacje, które działają w sposób ciągły, przez okresowe powiadamianie klientów o postępie, wyniki przyrostowe lub zmiany stanu.

Aby uzyskać więcej informacji na temat decydowania, kiedy obsługiwać wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).

## <a name="naming-asynchronous-methods"></a>Nazewnictwo metod asynchronicznych

Dla każdej metody synchronicznej *MethodName* , dla której chcesz dostarczyć odpowiednik asynchroniczny:

Zdefiniuj metodę _MethodName_**asynchroniczną** MethodName, która:

- Zwraca wartość `void`.

- Przyjmuje te same parametry co Metoda *MethodName* .

- Akceptuje wiele wywołań.

Opcjonalnie można zdefiniować Przeciążenie**Async** _MethodName_, identyczne z _MethodName_**Async**, ale z dodatkowym parametrem zwracającym obiekt `userState` . Zrób to, jeśli przygotowano się do zarządzania wieloma współbieżnymi wywołaniami metody, w tym przypadku `userState` wartość zostanie dostarczona do wszystkich programów obsługi zdarzeń w celu odróżnienia wywołań metody. Możesz również wybrać tę opcję po prostu w miejscu przechowywania stanu użytkownika w celu późniejszego pobrania.

Dla każdej oddzielnej sygnatury metody**asynchronicznej** _MethodName_:

1. Zdefiniuj następujące zdarzenie w tej samej klasie co Metoda:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Zdefiniuj następujących delegatów i <xref:System.ComponentModel.AsyncCompletedEventArgs> . Prawdopodobnie zostaną one zdefiniowane poza klasą, ale w tej samej przestrzeni nazw.

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

    - Upewnij się, że Klasa _MethodName_**CompletedEventArgs** uwidacznia jej składowe jako właściwości tylko do odczytu, a nie pola, jako że pola uniemożliwiają powiązanie danych.

    - Nie należy definiować <xref:System.ComponentModel.AsyncCompletedEventArgs> klas pochodnych dla metod, które nie generują wyników. Wystarczy użyć wystąpienia <xref:System.ComponentModel.AsyncCompletedEventArgs> samego siebie.

      > [!NOTE]
      > Jest to doskonale akceptowalne, gdy jest to możliwe i odpowiednie, aby ponownie użyć delegatów i <xref:System.ComponentModel.AsyncCompletedEventArgs> typów. W takim przypadku nazewnictwo nie będzie zgodne z nazwą metody, ponieważ dany delegat i <xref:System.ComponentModel.AsyncCompletedEventArgs> nie zostanie powiązany z pojedynczą metodą.

## <a name="optionally-support-cancellation"></a>Opcjonalna obsługa anulowania

Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, anulowanie powinno być uwidocznione na kliencie zgodnie z poniższym opisem. Należy pamiętać, że przed zdefiniowaniem pomocy technicznej dotyczącej anulowania należy wziąć pod uwagę dwa punkty decyzyjne:

- Czy Klasa, wraz z przyszłymi zaplanowanymi do niej dodatkami, ma tylko jedną operację asynchroniczną, która obsługuje anulowanie?

- Czy operacje asynchroniczne obsługujące anulowanie obsługują wiele oczekujących operacji? Oznacza to, że metoda _MethodName_**Async** MethodName przyjmuje `userState` parametr i zezwala na wielokrotne wywołania przed oczekiwaniem na zakończenie?

Użyj odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, co ma być sygnaturą dla metody anulowania.

### <a name="visual-basic"></a>Visual Basic

||Obsługiwane są liczne operacje jednoczesne|Tylko jedna operacja w danym momencie|
|------|------------------------------------------------|----------------------------------|
|Jedna operacja asynchroniczna w całej klasie|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Wiele operacji asynchronicznych w klasie|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Obsługiwane są liczne operacje jednoczesne|Tylko jedna operacja w danym momencie|
|------|------------------------------------------------|----------------------------------|
|Jedna operacja asynchroniczna w całej klasie|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Wiele operacji asynchronicznych w klasie|`void CancelAsync(object userState);`|`void CancelAsync();`|

W przypadku zdefiniowania `CancelAsync(object userState)` metody należy zachować ostrożność podczas wybierania ich wartości stanu, aby umożliwić im odróżnienie między wszystkimi metodami asynchronicznymi wywoływanymi na obiekcie, a nie tylko między wszystkimi wywołaniami pojedynczej metody asynchronicznej.

Decyzja o nazwie pojedynczej operacji asynchronicznej w wersji _MethodName_**AsyncCancel** opiera się na umożliwieniu łatwiejszej odnajdywania metody w środowisku projektowym, takim jak funkcja IntelliSense programu Visual Studio. Ta grupa pokrewnych członków i odróżnia je od innych członków, którzy nie mają nic do wykonania z funkcjami asynchronicznymi. Jeśli spodziewasz się, że w kolejnych wersjach można dodać dodatkowe operacje asynchroniczne, lepiej jest zdefiniować `CancelAsync` .

Nie należy definiować wielu metod z tabeli powyżej w tej samej klasie. To nie ma sensu lub będzie zasłaniać interfejs klasy z proliferacją metod.

Te metody zwykle zwracają natychmiast, a operacja może być w rzeczywistości niedozwolona. W obsłudze zdarzeń dla zdarzenia _MethodName_**ukończone** , obiekt _MethodName_**CompletedEventArgs** zawiera `Cancelled` pole, którego klienci mogą użyć do określenia, czy wystąpiło anulowanie.

Przestrzegaj semantyki anulowania opisanej w [najlepszych rozwiązaniach dotyczących implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-support-the-isbusy-property"></a>Opcjonalnie można obsługiwać Właściwość IsBusy

Jeśli Klasa nie obsługuje wielu współbieżnych wywołań, rozważ uwidocznienie `IsBusy` właściwości. Dzięki temu deweloperzy mogą określić, czy metoda**Async** _MethodName_jest uruchomiona bez przechwycenia wyjątku z metody _MethodName_**asynchronicznej** MethodName.

Przestrzegaj `IsBusy` semantyki opisanej w [najlepszych rozwiązaniach dotyczących implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-progress-reporting"></a>Opcjonalnie zapewniaj obsługę raportowania postępu

Jest on często pożądany w przypadku operacji asynchronicznej do raportowania postępu w trakcie jego działania. Wzorzec asynchroniczny oparty na zdarzeniach zawiera wytyczne umożliwiające wykonanie tej czynności.

- Opcjonalnie zdefiniuj zdarzenie, które ma zostać wywołane przez operację asynchroniczną i wywołane w odpowiednim wątku. <xref:System.ComponentModel.ProgressChangedEventArgs>Obiekt ma wskaźnik postępu o wartościach całkowitych, który powinien mieć wartość z przedziału od 0 do 100.

- Nazwij to zdarzenie w następujący sposób:

  - `ProgressChanged`Jeśli klasa ma wiele operacji asynchronicznych (lub można ją zwiększyć, aby uwzględnić wiele operacji asynchronicznych w przyszłych wersjach);

  - _MethodName_**ProgressChanged** , jeśli klasa ma pojedynczą operację asynchroniczną.

  To wybór nazywa się równoległą, która została wprowadzona dla metody anulowania, zgodnie z opisem w sekcji anulowanie pomocy technicznej.

To zdarzenie powinno używać <xref:System.ComponentModel.ProgressChangedEventHandler> podpisu delegata i <xref:System.ComponentModel.ProgressChangedEventArgs> klasy. Alternatywnie, jeśli można podać bardziej szczegółowy wskaźnik postępu dla domeny (na przykład odczytane bajty i całkowita liczba bajtów dla operacji pobierania), należy zdefiniować klasę pochodną <xref:System.ComponentModel.ProgressChangedEventArgs> .

Należy zauważyć, że dla klasy istnieje tylko jedno `ProgressChanged` lub _MethodName_zdarzenie**ProgressChanged** , niezależnie od liczby obsługiwanych przez nią metod asynchronicznych. Klienci powinni używać `userState` obiektu, który jest przesyłany do metod**asynchronicznych** _MethodName_, aby rozróżnić aktualizacje postępu dla wielu współbieżnych operacji.

Mogą wystąpić sytuacje, w których wiele operacji obsługuje postęp, a każdy z nich zwraca inny wskaźnik na potrzeby postępu. W takim przypadku pojedyncze `ProgressChanged` zdarzenie nie jest odpowiednie i można rozważyć obsługę wielu `ProgressChanged` zdarzeń. W takim przypadku należy użyć wzorca nazewnictwa _MethodName_**ProgressChanged** dla każdej metody**asynchronicznej** _MethodName_.

Przestrzegaj analizy postępu — opisane są [najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-returning-incremental-results"></a>Opcjonalnie zapewnić obsługę zwracania wyników przyrostowych

Czasami operacja asynchroniczna może zwrócić przyrostowe wyniki przed ukończeniem. Istnieje kilka opcji, których można użyć do obsługi tego scenariusza. Poniżej przedstawiono kilka przykładów.

### <a name="single-operation-class"></a>Klasa jednooperacji

Jeśli klasa obsługuje tylko pojedynczą operację asynchroniczną, a ta operacja może zwracać wyniki przyrostowe, wówczas:

- Rozszerzaj <xref:System.ComponentModel.ProgressChangedEventArgs> Typ, aby przenieść przyrostowe dane wynikowe, i zdefiniuj zdarzenie _MethodName_**ProgressChanged** z tymi rozszerzonymi danymi.

- Zgłoś to zdarzenie _MethodName_**ProgressChanged** , gdy istnieje przyrostowy wynik do raportowania.

To rozwiązanie dotyczy w odróżnieniu od klasy operacji pojedynczej asynchronicznej, ponieważ nie występuje problem z tym samym zdarzeniem, które ma zwrócić przyrostowe wyniki na "wszystkie operacje", ponieważ zdarzenie _MethodName_**ProgressChanged** .

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Klasa wielu operacji ze jednorodnymi wynikami przyrostowymi

W takim przypadku Klasa obsługuje wiele metod asynchronicznych, z których każda może zwracać wyniki przyrostowe, a wszystkie te same wyniki mają ten sam typ danych.

Postępuj zgodnie z modelem opisanym powyżej dla klas jednooperacji, ponieważ ta sama <xref:System.EventArgs> Struktura będzie działała dla wszystkich wyników przyrostowych. Zdefiniuj `ProgressChanged` zdarzenie zamiast zdarzenia _MethodName_**ProgressChanged** , ponieważ ma zastosowanie do wielu metod asynchronicznych.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Klasa wielu operacji z niejednorodnymi wynikami przyrostowymi

Jeśli klasa obsługuje wiele metod asynchronicznych, każdy zwraca inny typ danych, należy:

- Oddziel raportowanie wyników przyrostowych od raportów postępu.

- Zdefiniuj oddzielne zdarzenie _MethodName_**ProgressChanged** z odpowiednimi <xref:System.EventArgs> dla każdej metody asynchronicznej do obsługi danych przyrostowych wyniku tej metody.

Wywołaj ten program obsługi zdarzeń w odpowiednim wątku zgodnie z opisem w [temacie najlepsze rozwiązania dotyczące implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="handling-out-and-ref-parameters-in-methods"></a>Obsługa parametrów out i ref w metodach

Chociaż korzystanie z `out` i `ref` jest ogólnie zalecane w .NET Framework, poniżej przedstawiono reguły, które należy wykonać, gdy są obecne:

Nadana metoda synchroniczna *MethodName*:

- `out`parametry do *MethodName* nie powinny być częścią _MethodName_**Async**. Zamiast tego powinny one być częścią _MethodName_**CompletedEventArgs** o tej samej nazwie, co odpowiedni parametr w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).

- `ref`parametry do *MethodName* powinny być wyświetlane jako część _MethodName_**Async**MethodName, a jako część CompletedEventArgs _MethodName_**CompletedEventArgs** o takiej samej nazwie jak jej parametr odpowiedni w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).

Na przykład:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Metoda asynchroniczna i jej <xref:System.ComponentModel.AsyncCompletedEventArgs> Klasa będą wyglądać następująco:

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

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Instrukcje: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
