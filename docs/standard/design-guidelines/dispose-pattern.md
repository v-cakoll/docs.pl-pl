---
title: Wzorzec Dispose
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcb746ae2d8c2262b0cd0c6c9dcaababb12bd63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dispose-pattern"></a>Wzorzec Dispose
Wszystkie programy uzyskać jeden lub więcej zasobów systemowych, np. pamięci, systemu obsługuje lub połączenia z bazą danych w trakcie ich wykonanie. Deweloperzy muszą należy zachować ostrożność przy użyciu tych zasobów systemowych, ponieważ muszą zostać zwolnione po zostały zakupione i używane.  
  
 Środowisko CLR umożliwia automatyczne zarządzanie pamięcią. Pamięci zarządzanej (pamięci przydzielonej przy użyciu operatora C# `new`) nie trzeba jawnie zwolnione. Po uwolnieniu automatycznie przez moduł garbage collector (GC). Zwalnia deweloperzy z żmudnego i trudne zadanie zwolnienie pamięci i został jeden z głównych powodów wydajności Niespotykana zapewnianej przez program .NET Framework.  
  
 Niestety pamięci zarządzanej jest tylko jeden z wielu typów zasobów systemowych. Zasoby innych niż pamięci zarządzanej nadal należy zwolnić jawnie i są określane jako zasoby niezarządzane. GC specjalnie nie jest przeznaczone do zarządzania takich niezarządzanych zasobów, co oznacza, że odpowiedzialność za zarządzanie niezarządzanych zasobów znajduje się w ręce deweloperów.  
  
 Środowisko CLR zapewnia pomoc podczas zwalniania niezarządzanych zasobów. <xref:System.Object?displayProperty=nameWithType> deklaruje metody wirtualnej <xref:System.Object.Finalize%2A> (nazywanych również finalizatora) który jest wywoływany przez GC przed pamięci obiektu jest odzyskana przez wykaz Globalny i może zostać zastąpiona w celu zwolnić zasoby niezarządzane. Typy, które zastępować finalizatora są określane jako finalizable typów.  
  
 Mimo że finalizatory są efektywne w niektórych scenariuszach oczyszczania, mają dwa istotne wady:  
  
-   Finalizator jest wywoływana, gdy GC wykryje, że obiekt jest uprawniona do kolekcji. Dzieje się na niektórych nieokreślonej okresie po zasobu nie jest już potrzebne. Opóźnienie między po deweloper może lub chcesz zwolnić zasobu i czasu, gdy zasób jest rzeczywiście wydawanych przez finalizator może być niedopuszczalne w programach, które uzyskać wiele ograniczonych zasobów (zasoby, które można łatwo wyczerpane) lub w przypadki, w których zasoby są kosztowne do zachowania w użyciu (np. buforów dużych niezarządzanej pamięci).  
  
-   Gdy CLR musi wywoływać finalizator, musi Odłóż kolekcji pamięci obiektu, do czasu następnego zaokrąglona operacji wyrzucania elementów bezużytecznych (finalizatory Uruchom między kolekcji). Oznacza to, że pamięci obiektu (i wszystkie obiekty, które odwołuje się do) nie zostanie zwolnione przez okres dłuższy czas.  
  
 W związku z tym jednostki uzależnionej wyłącznie na finalizatory może nie być odpowiednie w wielu scenariuszach, jeśli ważne jest, aby odzyskać zasoby niezarządzane tak szybko jak to możliwe, podczas pracy nad ograniczonych zasobów lub w dużej wydajności scenariuszy, w którym dodano obciążenie GC zakończenia jest nie do przyjęcia.  
  
 Zapewnia platformę <xref:System.IDisposable?displayProperty=nameWithType> interfejsu, który powinien być zastosowany, aby umożliwić deweloperowi ręczne aby zwolnić zasoby niezarządzane, jak nie są wymagane. Zapewnia także <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> metodę, która może stwierdzić GC, który został ręcznie usunięty z obiektu i nie trzeba sfinalizowana, w którym to przypadku obiektu można odzyskać pamięci wcześniej. Typy, które implementują `IDisposable` interfejsu są określane jako typy usuwalne.  
  
 Wzorzec Dispose ma na celu standaryzacji użycia i stosowania finalizatory i `IDisposable` interfejsu.  
  
 Głównym celem wzorca jest uproszczeniu wykonania <xref:System.Object.Finalize%2A> i <xref:System.IDisposable.Dispose%2A> metody. Złożoność wynika z faktu, że metody udostępniania niektórych, ale nie wszystkie ścieżki kodu (różnice są opisane w dalszej części rozdziału). Ponadto istnieje historycznych przyczyn niektórych elementów powiązanych do zmiany języka obsługę zarządzania zasobami deterministyczne wzorca.  
  
 **CZY ✓** zaimplementować podstawowy wzorzec Dispose w typach zawierający wystąpienia typów, możliwe do rozporządzania. Zobacz [podstawowy wzorzec Dispose](#basic_pattern) sekcji szczegółowe informacje na temat podstawowych wzorca.  
  
 Jeśli typ jest odpowiedzialny za okres istnienia inne obiekty możliwe do rozporządzania, deweloperzy muszą mieć możliwość usunięcia ich zbyt. Za pomocą kontenera `Dispose` jest wygodny sposób, aby było to możliwe.  
  
 **CZY ✓** wdrożenia podstawowy wzorzec Dispose i zapewnić finalizator typów zawierający zasoby, które mają zostać zwolniony jawnie i które nie mają finalizatory.  
  
 Na przykład wzorzec powinny zostać wdrożone na typy buforów pamięci niezarządzanym przechowywania. [Finalizable typy](#finalizable_types) sekcji omówiono wskazówki związane z implementacją finalizatory.  
  
 **ROZWAŻ ✓** implementacja podstawowe wzorca Dispose klasy się nie przytrzymaj niezarządzane zasoby lub obiekty możliwe do rozporządzania ale prawdopodobnie podtypów, które wykonują.  
  
 Jest doskonałym przykładem <xref:System.IO.Stream?displayProperty=nameWithType> klasy. Abstrakcyjna klasa podstawowa, która nie zawiera żadnych zasobów, ale większość jej podklasach czy i w związku z tym implementuje tego wzorca.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Wzorzec Dispose podstawowe  
 Podstawowe implementacji wzorca obejmuje wykonania `System.IDisposable` interfejsu i typ deklarujący `Dispose(bool)` metodę, która implementuje całą logikę Oczyszczanie zasobów mogą być współużytkowane przez `Dispose` — metoda i opcjonalnie finalizatora.  
  
 W poniższym przykładzie przedstawiono prosty implementacji podstawowych wzorca:  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 Parametrów typu Boolean `disposing` wskazuje, czy metoda została wywołana z `IDisposable.Dispose` implementacji lub finalizatora. `Dispose(bool)` Implementacji należy sprawdzić parametr przed uzyskaniem dostępu do innych obiektów odwołania (np. pola zasobów w poprzednim przykładzie). Takie obiekty powinni mieć dostęp tylko wtedy, gdy metoda jest wywoływana z `IDisposable.Dispose` wdrożenia (gdy `disposing` parametru jest równa true). Jeśli metoda jest wywoływana z finalizatora (`disposing` ma wartość false), nie powinien być dostępny inne obiekty. Dzieje się tak że sfinalizowaniu obiektów w kolejności nieprzewidywalne i tak one lub ich zależności mogą już mieć sfinalizowany.  
  
 Ponadto ta sekcja dotyczy klasy z podstawowej, która już nie implementuje wzorzec Dispose. Jeśli możesz są dziedziczy z klasy, która już implementuje wzorzec, po prostu zastąpić `Dispose(bool)` metodę w celu zapewnienia dodatkowych zasobów oczyszczania logiki.  
  
 **CZY ✓** zadeklarować `protected virtual void Dispose(bool disposing)` metody, można scentralizować całą logikę związany ze zwalnianiem zasoby niezarządzane.  
  
 Oczyszczanie zasobów wszystkie powinien wystąpić w przypadku tej metody. Metoda jest wywoływana z obu finalizator i `IDisposable.Dispose` metody. Parametr nie będzie miał wartość false, jeśli jest wywoływany z wewnątrz finalizator. Stosuje się do upewnij się, że każdy kod działania podczas finalizacji nie uzyskuje dostęp do innych obiektów finalizable. Szczegóły dotyczące implementowania finalizatory są opisane w następnej sekcji.  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **CZY ✓** zaimplementować `IDisposable` interfejsu, wywołując po prostu `Dispose(true)` następuje `GC.SuppressFinalize(this)`.  
  
 Wywołanie `SuppressFinalize` może występować tylko, jeśli `Dispose(true)` wykonana pomyślnie.  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X nie** upewnij bez parametrów `Dispose` metody wirtualnej.  
  
 `Dispose(bool)` Metoda jest tą, która powinna zostać zastąpiona przez podklasy.  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X nie** zadeklarować wszystkie przeciążenia `Dispose` metody inne niż `Dispose()` i `Dispose(bool)`.  
  
 `Dispose` należy rozważyć słowem zastrzeżonym, ułatwia skodyfikować tego wzorca i uniknąć nieporozumień wśród implementacje, użytkowników i kompilatory. W przypadku niektórych języków może wybrać automatycznie Wdrażaj tego wzorca dla niektórych typów.  
  
 **CZY ✓** Zezwalaj `Dispose(bool)` metodę można wywołać więcej niż raz. Metoda może wybrać nic nie rób po pierwszym wywołaniu.  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X należy UNIKAĆ** Zgłaszanie wyjątku z poziomu `Dispose(bool)` z wyjątkiem sytuacji krytycznych gdzie zawierającego proces został uszkodzony (przecieków, niespójna udostępnionego itp.).  
  
 Użytkownicy oczekują, że wywołanie `Dispose` nie zgłosi wyjątku.  
  
 Jeśli `Dispose` może zgłosić wyjątek, dalsze logiki oczyszczania bloku finally nie zostanie wykonany. Aby obejść ten problem, użytkownik musi być zawijany każdego wywołania `Dispose` (wewnątrz bloku finally!) w bloku try, która prowadzi do obsługi oczyszczania bardzo złożonych. Jeśli wykonywania `Dispose(bool disposing)` metody, nigdy nie throw jako wyjątek, jeśli disposing ma wartość false. Dzięki temu zakończy proces, jeśli wykonywane w kontekście finalizatora.  
  
 **CZY ✓** throw <xref:System.ObjectDisposedException> z dowolnego elementu członkowskiego, który nie może zostać użyty obiekt został usunięty z.  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ ROZWAŻ** udostępnia metody `Close()`, oprócz `Dispose()`, jeśli jest blisko terminologii w obszarze.  
  
 Dzięki temu, ważne jest wykonanie `Close` taka sama jak implementacja `Dispose` i rozważ zaimplementowanie `IDisposable.Dispose` — metoda jawnie.  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Typy finalizable  
 Typy finalizable są typy, które rozszerzają podstawowe wzorzec Dispose zastępowanie finalizator i podając ścieżkę kodu finalizacji w `Dispose(bool)` metody.  
  
 Finalizatory są bardzo trudne do zaimplementowania poprawnie, przede wszystkim, ponieważ nie można wprowadzić pewne założenia (zwykle jest to prawidłowa) o stanie systemu podczas wykonywania. Poniższe wskazówki powinien brane pod uwagę zachować ostrożność.  
  
 Należy pamiętać, że niektóre wytycznych zastosowanie nie tylko do `Finalize` metody, ale dla kodu wywoływane z finalizator. W przypadku podstawowych Dispose wzorzec wcześniej zdefiniowane, oznacza to logikę, która wykonuje wewnątrz `Dispose(bool disposing)` podczas `disposing` parametr ma wartość false.  
  
 Jeśli już klasa podstawowa jest finalizable i implementuje wzorzec Dispose podstawowe, należy nie zastępują `Finalize` ponownie. Zamiast tego należy po prostu zastąpić `Dispose(bool)` metodę w celu zapewnienia dodatkowych zasobów oczyszczania logiki.  
  
 Poniższy kod przedstawia przykład finalizable typu:  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X należy UNIKAĆ** wprowadzania finalizable typów.  
  
 Należy rozważyć w każdym przypadku, w którym uważasz, że wymagane jest finalizator. Brak rzeczywistych kosztów związanych z wystąpień finalizatory z punktu widzenia złożoności wydajności i kod. Preferowane jest przy użyciu otoki zasobów, takich jak <xref:System.Runtime.InteropServices.SafeHandle> aby hermetyzować zasoby niezarządzane, jeśli jest to możliwe, w którym to przypadku finalizator staje się niepotrzebne ponieważ otoka jest odpowiedzialny za własną Oczyszczanie zasobów.  
  
 **X nie** tworzenie finalizable typów wartości.  
  
 Tylko typy referencyjne uzyskać faktycznie opracowane przez środowisko CLR, a w związku z tym każda próba umieść finalizator na typ wartości zostaną zignorowane. C# i kompilatory C++ wymusić tę regułę.  
  
 **CZY ✓** upewnij typu finalizable, jeśli typ jest odpowiedzialny za zwolnienie niezarządzanego zasobu, który nie ma własną finalizatora.  
  
 Podczas implementowania finalizator, po prostu Wywołaj `Dispose(false)` i umieść całą logikę Oczyszczanie zasobów wewnątrz `Dispose(bool disposing)` metody.  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **CZY ✓** wdrożenia dla każdego typu finalizable podstawowy wzorzec Dispose.  
  
 Dzięki temu użytkownicy typu sposób jawnie przeprowadzi deterministyczne Oczyszczanie tych samych zasobów, za które odpowiada finalizatora.  
  
 **X nie** uzyskać dostępu do żadnych obiektów finalizable w ścieżce kodu finalizator, ponieważ istnieje duże ryzyko, że ich będzie mieć już sfinalizowany.  
  
 Na przykład obiekt finalizable A, który zawiera odwołanie do innego obiektu finalizable B niezawodnie nie można użyć B w A finalizator, albo na odwrót. Finalizatory są wywoływane w kolejności losowej (zbyt mała słabe gwarancji porządkowania finalizacji krytyczne).  
  
 Ponadto należy pamiętać, że obiekty przechowywane w zmienne statyczne będą uzyskać zbierane w niektórych punktach podczas zwalniania domeny aplikacji lub podczas zamykania procesu. Uzyskiwanie dostępu do zmienną statyczną, która odwołuje się do obiektu finalizable (lub wywołanie metody statycznej, który może używać wartości przechowywane w zmiennych statycznych) może nie być bezpieczne w przypadku <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> zwraca wartość true.  
  
 **CZY ✓** upewnij Twojej `Finalize` metody chronione.  
  
 C#, C++ i VB.NET deweloperzy nie ma potrzeby martwić się o to, ponieważ kompilatory pomóc wymusić Niniejsze wytyczne.  
  
 **X nie** escape let wyjątki od logiki finalizator, z wyjątkiem błędy krytyczne systemu.  
  
 Jeśli finalizator jest zgłaszany wyjątek, aparat CLR spowoduje zamknięcie cały proces (począwszy od platformy .NET Framework w wersji 2.0), inne finalizatory uniemożliwia wykonywanie i zasobów z został wydany w kontrolowany sposób.  
  
 **ROZWAŻ ✓** tworzenie i używanie obiektu finalizable krytycznego (typ z hierarchii typów, który zawiera <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) w sytuacjach, w których finalizator bezwzględnie wykonać nawet w wypadku zwalnia domeny wymuszone aplikacji i wątków przerywa.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
