---
title: Wzorzec Dispose
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: KrzysztofCwalina
ms.openlocfilehash: ee6e9898ae93e2e6628eadec150a3c9c05f5d9c5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147720"
---
# <a name="dispose-pattern"></a>Wzorzec Dispose
Wszystkie programy uzyskuje jeden lub więcej zasobów systemowych, takich jak pamięć, systemu lub połączenia z bazą danych w trakcie ich wykonywania. Deweloperzy muszą należy zachować ostrożność, korzystając z takich zasobów systemowych, ponieważ muszą zostać zwolnione po zostały nabyte i używane.  
  
 Środowisko CLR zapewnia obsługę automatyczne zarządzanie pamięcią. Pamięci zarządzanej (pamięci przydzielonej za pomocą operatora C# `new`) nie należy jawnie zwolnić. Jest on zwalniany automatycznie przez moduł odśmiecania pamięci (GC). To ułatwia deweloperom z żmudnym i trudne zadanie zwalnianie pamięci i był jednym z głównych powodów wyjątkowej produktywności zapewnianej przez program .NET Framework.  
  
 Niestety pamięci zarządzanej jest tylko jeden z wielu typów zasobów systemowych. Zasobów innych niż pamięci zarządzanej nadal należy jawnie zwolnić i są określane jako niezarządzane zasoby. Wykaz Globalny specjalnie nie jest przeznaczone do zarządzania takich niezarządzanych zasobów, co oznacza, że odpowiedzialność za zarządzanie niezarządzane zasoby znajdujące się w rękach deweloperów.  
  
 Środowisko CLR oferuje pomoc podczas zwalniania niezarządzanych zasobów. <xref:System.Object?displayProperty=nameWithType> deklaruje metodę wirtualną <xref:System.Object.Finalize%2A> (nazywane również finalizatora) który jest wywoływany przez GC przed pamięci obiektu jest odzyskiwane w ramach odzyskiwania pamięci i może zostać zastąpiona w celu zwolnienia zasobów niezarządzanych. Typy, które zastępują finalizator są określane jako typy sfinalizowania.  
  
 Mimo że finalizatory są efektywne w niektórych scenariuszach oczyszczania, mają dwie istotne wady:  
  
-   Finalizator jest wywoływana, gdy GC wykryje, że obiekt jest kwalifikuje się do kolekcji. Dzieje się pewnego okresu nieokreślony czas po zasobu nie jest już potrzebna. Opóźnienie między gdy deweloper można lub uzyskać dostęp do zwolnienia zasobu i czasu, gdy zasób jest faktycznie wydane przez finalizator może być niedopuszczalne w programach, które pobierać wiele ograniczonych zasobów (zasoby, które można łatwo wyczerpane) lub w przypadki, w których zasoby są kosztowne zachować używane (np. buforów dużych niezarządzanej pamięci).  
  
-   Gdy środowisko CLR musi wywołać finalizatora, należy odłożyć kolekcji pamięci obiektu, do czasu następnego zaokrąglanie wyrzucania elementów bezużytecznych (finalizatory Uruchom między operacjami). Oznacza to, że obiekt pamięci (i wszystkich obiektów, odwołuje się do) nie zostanie zwolnione przez dłuższy czas.  
  
 W związku z tym, opierając się wyłącznie na finalizatory mogą nie być odpowiednie w wielu scenariuszach, gdy ważne jest, aby odzyskać niezarządzane zasoby tak szybko, jak to możliwe, podczas pracy z ograniczonych zasobów lub w wysoce wydajnych scenariuszach, w którym dodano obciążenie GC Finalizacja jest nie do przyjęcia.  
  
 Udostępnia platformę <xref:System.IDisposable?displayProperty=nameWithType> interfejs, który należy wdrożyć umożliwiają deweloperowi ręcznie zwolnić niezarządzane zasoby, jak tylko nie są wymagane. Zapewnia także <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodę, która może sprawdzić GC został ręcznie usunięty z obiektu i nie trzeba można sfinalizować, w którym to przypadku obiektu można odzyskać pamięci wcześniej. Typami, które implementują `IDisposable` interfejsu są określane jako typy możliwe do likwidacji.  
  
 Wzorzec usuwania ma na celu standaryzacji użycie i wdrożenie finalizatory i `IDisposable` interfejsu.  
  
 Głównym celem dla wzorca ma złożoność wdrożenia <xref:System.Object.Finalize%2A> i <xref:System.IDisposable.Dispose%2A> metody. Złożoność wynika z faktu, że metody udostępniania niektórych, ale nie wszystkie ścieżki kodu (różnice są opisane w dalszej części rozdziału). Ponadto istnieją historycznych przyczyny niektóre elementy wzorzec związanymi z ewolucją Obsługa języka dla funkcji zarządzania zasobami deterministyczna.  
  
 **✓ DO** zaimplementować podstawowy wzorzec Dispose w typach zawierający wystąpienia typów, możliwe do rozporządzania. Zobacz [podstawowy wzorzec Dispose](#basic_pattern) sekcji, aby uzyskać szczegółowe informacje na temat podstawowy wzorzec.  
  
 Jeśli typ jest odpowiedzialny za okres istnienia inne obiekty możliwe do rozporządzania, deweloperzy muszą mieć do rozporządzania, zbyt. Za pomocą kontenera `Dispose` metodą jest wygodny sposób, aby było to możliwe.  
  
 **✓ DO** wdrożenia podstawowy wzorzec Dispose i zapewnić finalizator typów zawierający zasoby, które mają zostać zwolniony jawnie i które nie mają finalizatory.  
  
 Na przykład wzorzec powinny zostać wdrożone na typach niezarządzanej pamięci, buforów przechowywania. [Sfinalizowania typy](#finalizable_types) sekcji omówiono wskazówki związane z implementacją finalizatorów.  
  
 **✓ CONSIDER** implementacja podstawowe wzorca Dispose klasy się nie przytrzymaj niezarządzane zasoby lub obiekty możliwe do rozporządzania ale prawdopodobnie podtypów, które wykonują.  
  
 Doskonałe przykładem jest <xref:System.IO.Stream?displayProperty=nameWithType> klasy. Abstrakcyjna klasa bazowa, która nie ma żadnych zasobów, ale większość jej podklasach czy i w związku z tym implementuje ten wzorzec.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Wzorzec usuwania podstawowe  
 Podstawową implementację wzorca obejmuje wdrażanie `System.IDisposable` interfejsu i deklarowanie `Dispose(bool)` metody, która implementuje całą logikę Oczyszczanie zasobów, aby współdzielić je między `Dispose` metody i opcjonalnie finalizatora.  
  
 Proste wdrażanie wzorca podstawowego można znaleźć w poniższym przykładzie:  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Parametr logiczny `disposing` wskazuje, czy metoda została wywołana z `IDisposable.Dispose` implementacji lub finalizatora. `Dispose(bool)` Implementacji należy sprawdzić parametr przed uzyskaniem dostępu do innych obiektów odwołania (np. pole zasobu w poprzednim przykładzie). Takie obiekty powinny zostać oceniony jedynie, gdy metoda jest wywoływana z `IDisposable.Dispose` wdrożenia (gdy `disposing` parametr jest równa true). Jeśli metoda jest wywoływana z finalizatora (`disposing` ma wartość false), nie powinien być dostępny innych obiektów. Przyczyną jest, że obiekty sfinalizowaniu w kolejności nieprzewidywalne i dlatego ich lub dowolnej ich zależności mogą już mieć sfinalizowany.  
  
 Ponadto w tej sekcji dotyczy klasach z atrybutem podstawowy, który już nie implementuje wzorzec Dispose. Jeśli dziedziczą z klasy, która już implementuje wzorzec, po prostu zastąpić `Dispose(bool)` metodę, aby zapewnić logikę oczyszczania dodatkowych zasobów.  
  
 **✓ DO** zadeklarować `protected virtual void Dispose(bool disposing)` metody, można scentralizować całą logikę związany ze zwalnianiem zasoby niezarządzane.  
  
 Czyszczenie wszystkich zasobów powinien wystąpić w przypadku tej metody. Metoda jest wywoływana z obu finalizator i `IDisposable.Dispose` metody. Parametr nie będzie miał wartość false, jeśli jest wywoływany z wewnątrz finalizatora. Stosuje się do upewnij się, że każdy kod uruchomiony podczas finalizacji nie uzyskuje dostęp do innych obiektów sfinalizowania. Szczegóły dotyczące implementowania finalizatory są opisane w następnej sekcji.  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** zaimplementować `IDisposable` interfejsu, wywołując po prostu `Dispose(true)` następuje `GC.SuppressFinalize(this)`.  
  
 Wywołanie `SuppressFinalize` powinna występować tylko w przypadku `Dispose(true)` wykonuje z powodzeniem.  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X DO NOT** upewnij bez parametrów `Dispose` metody wirtualnej.  
  
 `Dispose(bool)` Metody jest tą, która powinna zostać zastąpiona przez podklasy.  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 **X DO NOT** zadeklarować wszystkie przeciążenia `Dispose` metody inne niż `Dispose()` i `Dispose(bool)`.  
  
 `Dispose` należy rozważyć słowem zastrzeżonym, ułatwiające skodyfikować tego wzorca i uniknąć nieporozumień wśród implementacje, użytkowników i kompilatory. W przypadku niektórych języków może wybrać automatycznie implementacja tego wzorca od niektórych typów.  
  
 **✓ DO** Zezwalaj `Dispose(bool)` metodę można wywołać więcej niż raz. Metoda może wybrać nic nie rób po pierwszym wywołaniu.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X AVOID** Zgłaszanie wyjątku z poziomu `Dispose(bool)` z wyjątkiem sytuacji krytycznych gdzie zawierającego proces został uszkodzony (przecieków, niespójna udostępnionego itp.).  
  
 Użytkownicy oczekują, że wywołanie `Dispose` nie zgłosi wyjątek.  
  
 Jeśli `Dispose` może zgłosić wyjątek, dalsze logiki oczyszczania blok finally nie zostanie wykonany. Aby obejść ten problem, użytkownik będzie musiał opakować każde wywołanie `Dispose` (w ramach bloku finally!) w bloku try, co prowadzi do obsługi bardzo złożonych oczyszczania. Jeśli wykonywane `Dispose(bool disposing)` metody, nigdy nie throw wyjątek, jeśli disposing ma wartość false, który. To zakończenie procesu jeśli wykonywane w kontekście finalizatora.  
  
 **✓ DO** throw <xref:System.ObjectDisposedException> z dowolnego elementu członkowskiego, który nie może zostać użyty obiekt został usunięty z.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ CONSIDER** udostępnia metody `Close()`, oprócz `Dispose()`, jeśli jest blisko terminologii w obszarze.  
  
 Po wykonaniu tej czynności jest ważne, `Close` taka sama jak implementacja `Dispose` i rozważ zaimplementowanie `IDisposable.Dispose` metoda jawnie.  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Typy sfinalizowania  
 Typy sfinalizowania są typy, które rozszerzają podstawowy wzorzec Dispose zastępowanie finalizator i podając ścieżkę kodu finalizacji w `Dispose(bool)` metody.  
  
 Finalizatory są bardzo trudne do zaimplementowania poprawnie, przede wszystkim, ponieważ niektóre (zwykle jest to ważny) założeń dotyczących stanu systemu nie może wprowadzać podczas ich wykonywania. Szczególną uwagę należy uwzględnić poniższe zalecenia.  
  
 Należy pamiętać, że niektóre wytyczne mają zastosowanie nie tylko do `Finalize` metody, ale na wszelki kod wywołuje z finalizatora. W przypadku podstawowy Dispose wzorzec uprzednio zdefiniowany, oznacza to, że logika, która wykonuje wewnątrz `Dispose(bool disposing)` podczas `disposing` parametr ma wartość false.  
  
 Jeśli klasa bazowa już jest sfinalizowania, implementuje podstawowy wzorzec Dispose nie powinna zostać przesłonięta `Finalize` ponownie. Zamiast tego należy po prostu zastąpić `Dispose(bool)` metodę, aby zapewnić logikę oczyszczania dodatkowych zasobów.  
  
 Poniższy kod przedstawia przykład sfinalizowania typu:  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X AVOID** wprowadzania finalizable typów.  
  
 Zastanów się uważnie każdy przypadek, w którym uważasz, że finalizator jest wymagana. Ma faktycznego koszt związany z wystąpień finalizatory z punktu widzenia złożoności wydajności i kodu. Preferuj przy użyciu otoki zasobów, takich jak <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzowania niezarządzanych zasobów, jeśli jest to możliwe, w którym to przypadku finalizatora staje się niepotrzebne ponieważ otoki jest odpowiedzialny za własne czyszczenie zasobów.  
  
 **X DO NOT** tworzenie finalizable typów wartości.  
  
 Tylko typy odwołań Pobierz faktycznie zatwierdzony przez środowisko CLR i zignorowana każda próba umieścić finalizatora dla typu wartości. Kompilatory C# i C++ wymuszają tę regułę.  
  
 **✓ DO** upewnij typu finalizable, jeśli typ jest odpowiedzialny za zwolnienie niezarządzanego zasobu, który nie ma własną finalizatora.  
  
 Podczas implementowania finalizator, wystarczy wywołać `Dispose(false)` i umieść całą logikę Oczyszczanie zasobów wewnątrz `Dispose(bool disposing)` metody.  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 **✓ DO** wdrożenia dla każdego typu finalizable podstawowy wzorzec Dispose.  
  
 Dzięki temu użytkownicy typu oznacza jawnie Przeprowadź czyszczenie deterministyczne tych samych zasobów, za które odpowiada finalizator.  
  
 **X DO NOT** uzyskać dostępu do żadnych obiektów finalizable w ścieżce kodu finalizator, ponieważ istnieje duże ryzyko, że ich będzie mieć już sfinalizowany.  
  
 Na przykład, które można sfinalizować obiekt A, który odwołuje się do innego obiektu sfinalizowania B niezawodnie nie można użyć B w A finalizatora, lub na odwrót. Finalizatory są wywoływane w kolejności losowej (ograniczony słabe gwarancja szeregowania krytyczna finalizacja).  
  
 Ponadto należy pamiętać, że obiekty przechowywane w zmiennych statycznych będą Pobierz zbierane w niektórych punktach podczas zwalniania domeny aplikacji lub w trakcie proces zostanie zakończony. Uzyskiwanie dostępu do zmienną statyczną, która odwołuje się do sfinalizowania obiektu (lub wywoływania statycznej metody, która może korzystać wartości przechowywane w zmiennych statycznych) może nie być bezpieczne, jeśli <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> zwraca wartość true.  
  
 **✓ DO** upewnij Twojej `Finalize` metody chronione.  
  
 Programiści języka C#, C++ i VB.NET nie są już martwić się o to, ponieważ kompilatory pomóc wymusić niniejszych wytycznych.  
  
 **X DO NOT** escape let wyjątki od logiki finalizator, z wyjątkiem błędy krytyczne systemu.  
  
 Jeśli wyjątek jest zgłaszany z finalizatora, środowisko CLR spowoduje wyłączenie całego procesu (począwszy od .NET Framework w wersji 2.0), inne finalizatory uniemożliwia wykonywanie i zasoby z udostępniane w sposób kontrolowany.  
  
 **✓ CONSIDER** tworzenie i używanie obiektu finalizable krytycznego (typ z hierarchii typów, który zawiera <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) w sytuacjach, w których finalizator bezwzględnie wykonać nawet w wypadku zwalnia domeny wymuszone aplikacji i wątków przerywa.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
