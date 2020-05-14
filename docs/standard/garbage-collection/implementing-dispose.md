---
title: Implementacja metody Dispose
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: a002e0d27dfe28795b28e6813c4f5d5b3e13cdaf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396903"
---
# <a name="implement-a-dispose-method"></a>Implementacja metody Dispose

Implementowanie <xref:System.IDisposable.Dispose%2A> metody jest przede wszystkim przeznaczone do zwalniania niezarządzanych zasobów używanych przez kod. Podczas pracy z elementami członkowskimi wystąpień <xref:System.IDisposable> , które są implementacjami, często są to wywołania kaskadowe <xref:System.IDisposable.Dispose%2A> . Istnieją dodatkowe przyczyny implementacji <xref:System.IDisposable.Dispose%2A> , takie jak cofnięcie wcześniej wykonanego działania. Na przykład zwalnianie pamięci, która została przypisana, usunięcie elementu z kolekcji, która została dodana, sygnalizowanie wydania blokady, która została pobrana itd.

[Moduł wyrzucania elementów bezużytecznych platformy .NET](index.md) nie przydziela lub nie zwalnia pamięci niezarządzanej. Wzorzec do usuwania obiektu, nazywany wzorcem usuwania, nakłada kolejność na okres istnienia obiektu. Wzorzec Dispose jest używany dla obiektów implementujących <xref:System.IDisposable> interfejs i jest powszechny w przypadku współpracy z uchwytami plików i potoków, dojściami do rejestru, dojściami oczekiwania lub wskaźnikami do bloków pamięci niezarządzanej. Dzieje się tak, ponieważ moduł wyrzucania elementów bezużytecznych nie może odzyskiwać obiektów niezarządzanych.

Aby zapewnić, że zasoby są zawsze odpowiednio czyszczone, <xref:System.IDisposable.Dispose%2A> Metoda powinna być idempotentne, tak że jest ona wielokrotnie wywoływana bez zgłaszania wyjątku. Ponadto kolejne wywołania elementu <xref:System.IDisposable.Dispose%2A> nie powinny nic robić.

Przykład kodu podany dla <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metody pokazuje, jak wyrzucanie elementów bezużytecznych może spowodować uruchomienie finalizatora, podczas gdy niezarządzane odwołanie do obiektu lub jego członków jest nadal w użyciu. Warto mieć sens, <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> Aby obiekt nieuprawniony do wyrzucania elementów bezużytecznych od początku bieżącej procedury do punktu, w którym ta metoda jest wywoływana.

## <a name="safe-handles"></a>Bezpieczne dojścia

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. Dlatego zalecamy konstruowanie <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> obiektów zamiast implementowania finalizatora.

A <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> jest abstrakcyjnym typem zarządzanym, który otacza obiekt <xref:System.IntPtr?displayProperty=nameWithType> , który identyfikuje niezarządzany zasób. W systemie Windows może on identyfikować dojście w systemie UNIX, deskryptor pliku. Zapewnia ona wszystkie wymagane logiki, aby zapewnić, że ten zasób jest wystawiony raz i tylko raz, gdy `SafeHandle` zostanie usunięty lub gdy wszystkie odwołania do `SafeHandle` zostały usunięte, a `SafeHandle` wystąpienie zostanie sfinalizowane.

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>Jest abstrakcyjną klasą bazową. Klasy pochodne zapewniają określone wystąpienia dla różnych rodzajów uchwytów. Te klasy pochodne sprawdzają, jakie wartości <xref:System.IntPtr?displayProperty=nameWithType> są uważane za nieprawidłowe i jak ostatecznie zwolnić dojście. Na przykład podaje <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> `SafeHandle` się do zawijania, `IntPtrs` który identyfikuje otwarte dojścia do pliku/deskryptory, i zastępuje jego <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle?displayProperty=nameWithType> metodę, aby zamknąć (za pośrednictwem `close` funkcji w systemie UNIX lub `CloseHandle` funkcji systemu Windows). Większość interfejsów API w bibliotekach platformy .NET, które tworzą zasób niezarządzany, będzie otoczyć ją w `SafeHandle` i zwrócić `SafeHandle` do Ciebie w razie potrzeby, zamiast wycofać pierwotny wskaźnik. W sytuacjach, w których można korzystać z niezarządzanego składnika i uzyskać `IntPtr` dla niezarządzanego zasobu, można utworzyć własny `SafeHandle` Typ, aby go otoczyć. W związku z `SafeHandle` tym kilka typów niewymagających zaimplementowania finalizatorów; Większość implementacji wzorców jednorazowych kończy Zawijanie innych zarządzanych zasobów, z których część może być `SafeHandle` s.

Następujące klasy pochodne w <xref:Microsoft.Win32.SafeHandles> przestrzeni nazw zapewniają bezpieczne dojścia:

- <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>Klasy, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> , i <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> , dla plików, plików mapowanych na pamięć i potoków.
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>Klasa dla widoków pamięci.
- <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>Klasy, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> i <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> , dla konstrukcji kryptografii.
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle>Klasa dla kluczy rejestru.
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>Klasa, dla uchwytów oczekiwania.

## <a name="dispose-and-disposebool"></a>Dispose () i Dispose (bool)

<xref:System.IDisposable>Interfejs wymaga implementacji pojedynczej metody bez parametrów <xref:System.IDisposable.Dispose%2A> . Ponadto każda klasa Niezapieczętowana powinna mieć dodatkową `Dispose(bool)` metodę przeciążenia, która ma być zaimplementowana:

- `public`Implementacja niewirtualna ( `NonInheritable` w Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , która nie ma parametrów.

- `protected virtual`Metoda ( `Overridable` w Visual Basic), `Dispose` której sygnatura:

  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]

  > [!IMPORTANT]
  > `disposing`Parametr powinien być `false` wywoływany z finalizatora i `true` wywoływany z <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody. Innymi słowy, jest to w `true` przypadku niejednoznacznego wywoływania i w `false` przypadku, gdy jest wywoływana niejednoznacznie.

### <a name="the-dispose-method"></a>Metoda Dispose ()

Ponieważ `public` , niewirtualne ( `NonInheritable` w Visual Basic), Metoda bez parametrów `Dispose` jest wywoływana przez odbiorcę typu, jego celem jest zwolnienie niezarządzanych zasobów, wykonanie ogólnego oczyszczania i wskazanie, że finalizator, jeśli taki istnieje, nie musi być uruchamiany. Zwalnianie rzeczywistej pamięci skojarzonej z obiektem zarządzanym jest zawsze domeną [modułu wyrzucania elementów bezużytecznych](index.md). Z tego powodu ma standardową implementację:

[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]

`Dispose`Metoda wykonuje wszystkie operacje czyszczenia obiektów, dlatego Moduł wyrzucania elementów bezużytecznych nie musi już wywoływać <xref:System.Object.Finalize%2A?displayProperty=nameWithType> przesłonięcia obiektów. W związku z tym wywołanie <xref:System.GC.SuppressFinalize%2A> metody uniemożliwia uruchomienie finalizatora przez moduł wyrzucania elementów bezużytecznych. Jeśli typ nie ma finalizatora, wywołanie nie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> ma żadnego wpływu. Należy zauważyć, że rzeczywiste oczyszczanie jest wykonywane przez `Dispose(bool)` Przeciążenie metody.

### <a name="the-disposebool-method-overload"></a>Przeciążenie metody Dispose (bool)

W przypadku przeciążenia `disposing` parametr jest <xref:System.Boolean> wskazuje, czy wywołanie metody pochodzi z <xref:System.IDisposable.Dispose%2A> metody (jej wartość jest `true` ) czy z finalizatora (jego wartość to `false` ).

Treść metody składa się z dwóch bloków kodu:

- Blok zwalniający niezarządzane zasoby. Ten blok jest wykonywany niezależnie od wartości `disposing` parametru.
- Blok warunkowy zwalniający zarządzane zasoby. Ten blok jest wykonywany, gdy wartość `disposing` jest `true` . Zarządzane zasoby, które zwalnia, to m.in.:

  - **Obiekty zarządzane, które implementują <xref:System.IDisposable> .** Bloku warunkowego można użyć do wywołania ich <xref:System.IDisposable.Dispose%2A> implementacji (kaskadowego Dispose). Jeśli użyto klasy pochodnej <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> , aby otoczyć niezarządzany zasób, należy wywołać <xref:System.Runtime.InteropServices.SafeHandle.Dispose?displayProperty=nameWithType> implementację tutaj.

  - **Zarządzane obiekty, które zużywają duże ilości pamięci lub zużywają niewystarczające zasoby.** Przypisz do nich duże odwołania do obiektów zarządzanych, aby `null` zwiększyć ich dostępność. Te wersje są szybsze, niż gdyby były odzyskiwane w sposób Niedeterministyczny.

Jeśli wywołanie metody pochodzi od finalizatora, należy wykonać tylko kod, który zwolni niezarządzane zasoby. Realizator jest odpowiedzialny za zapewnienie, że ścieżka fałszywa nie współdziała z zarządzanymi obiektami, które mogły zostać ododzyskiwane. Jest to ważne, ponieważ kolejność, w której moduł zbierający elementy bezużyteczne niszczy obiekty zarządzane podczas finalizowania, nie jest deterministyczna.

## <a name="cascade-dispose-calls"></a>Kaskadowe wywołania Dispose

Jeśli klasa jest własnością pola lub właściwości, a jej typ implementuje <xref:System.IDisposable> , należy również zaimplementować zawierającą ją klasę <xref:System.IDisposable> . Klasa, która tworzy wystąpienie <xref:System.IDisposable> implementacji i zapisuje ją jako element członkowski wystąpienia, jest również odpowiedzialna za jego czyszczenie. Jest to pomocne w zapewnieniu, że odwołania do typów jednorazowych, których dotyczy odwołanie, są nadawane za pomocą <xref:System.IDisposable.Dispose%2A> metody. W tym przykładzie Klasa jest `sealed` (lub `NotInheritable` w Visual Basic).

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/disposable1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/disposable1.vb#1)]

## <a name="implement-the-dispose-pattern"></a>Implementowanie wzorca usuwania

Wszystkie niezapieczętowane klasy lub (Visual Basic klas, które nie zostały zmodyfikowane jako `NotInheritable` ), powinny być uważane za potencjalną klasę bazową, ponieważ mogą być dziedziczone. W przypadku zaimplementowania wzorca usuwania dla dowolnej potencjalnej klasy podstawowej należy podać następujące elementy:

- <xref:System.IDisposable.Dispose%2A>Implementacja, która wywołuje `Dispose(bool)` metodę.
- `Dispose(bool)`Metoda, która wykonuje rzeczywiste oczyszczanie.
- Klasa pochodna, <xref:System.Runtime.InteropServices.SafeHandle> która otacza niezarządzany zasób (zalecane) lub przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle>Klasa zawiera finalizator, więc nie trzeba pisać siebie.

> [!IMPORTANT]
> Klasa bazowa może odwoływać się tylko do obiektów zarządzanych i zaimplementować wzorzec Dispose. W takich przypadkach finalizator jest niepotrzebny. Finalizator jest wymagany tylko w przypadku bezpośredniego odwoływania się do zasobów niezarządzanych.

Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która używa bezpiecznego dojścia.

[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]

> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu do zilustrowania wzorca; zamiast tego można użyć dowolnego obiektu pochodnego <xref:System.Runtime.InteropServices.SafeHandle> . Należy zauważyć, że przykład nie tworzy prawidłowo wystąpienia <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.

Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType> .

[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]

> [!TIP]
> W języku C# tworzysz [finalizator](../../csharp/programming-guide/classes-and-structs/destructors.md) przez zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . W Visual Basic jest to realizowane za pomocą `Protected Overrides Sub Finalize()` .

## <a name="implement-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasa pochodna klasy, która implementuje <xref:System.IDisposable> Interfejs <xref:System.IDisposable> , nie należy implementować, ponieważ Implementacja klasy bazowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jest dziedziczona przez klasy pochodne. Zamiast tego, aby oczyścić klasę pochodną, należy podać następujące elementy:

- `protected override void Dispose(bool)`Metoda, która zastępuje metodę klasy bazowej i wykonuje rzeczywiste oczyszczanie klasy pochodnej. Ta metoda musi również wywołać `base.Dispose(bool)` metodę ( `MyBase.Dispose(bool)` w Visual Basic) klasy bazowej i przekazać jej stan likwidacji dla tego argumentu.
- Klasa pochodna, <xref:System.Runtime.InteropServices.SafeHandle> która otacza niezarządzany zasób (zalecane) lub przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle>Klasa zawiera finalizator, który uwalnia Cię do kodu. Jeśli podasz finalizator, musi on wywołać `Dispose(bool)` Przeciążenie z `disposing` argumentem `false` .

Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:

[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]

> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu do zilustrowania wzorca; zamiast tego można użyć dowolnego obiektu pochodnego <xref:System.Runtime.InteropServices.SafeHandle> . Należy zauważyć, że przykład nie tworzy prawidłowo wystąpienia <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.

Oto ogólny wzorzec implementowania wzorca usuwania dla klasy pochodnej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType> :

[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]

## <a name="implement-the-dispose-pattern-with-safe-handles"></a>Implementowanie wzorca Dispose z bezpiecznymi dojściami

Poniższy przykład ilustruje wzorzec Dispose dla klasy bazowej, `DisposableStreamResource` który używa bezpiecznego dojścia do hermetyzowania niezarządzanych zasobów. Definiuje `DisposableStreamResource` klasę, która używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do zawijania <xref:System.IO.Stream> obiektu, który reprezentuje otwarty plik. Klasa zawiera również pojedynczą właściwość, `Size` która zwraca łączną liczbę bajtów w strumieniu pliku.

[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]

## <a name="implement-the-dispose-pattern-for-a-derived-class-with-safe-handles"></a>Implementowanie wzorca usuwania dla klasy pochodnej z bezpiecznymi dojściami

Poniższy przykład ilustruje wzorzec usuwania dla klasy pochodnej, `DisposableStreamResource2` która dziedziczy z `DisposableStreamResource` klasy przedstawionej w poprzednim przykładzie. Klasa dodaje dodatkową metodę, `WriteFileInfo` i używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu do zawijania uchwytu zapisywalnego pliku.

[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]

## <a name="see-also"></a>Zobacz także

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Wzorzec Dispose](implementing-dispose.md)
