---
title: Implementowanie metody Dispose
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 964c788c5fc1ac791ed3ddd20c9c5c972d07b2c1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106889"
---
# <a name="implementing-a-dispose-method"></a>Implementowanie metody Dispose

Zaimplementuj <xref:System.IDisposable.Dispose%2A> metodę zwalniania niezarządzanych zasobów używanych przez aplikację. Moduł wyrzucania elementów bezużytecznych platformy .NET nie przydziela lub nie zwalnia pamięci niezarządzanej.  
  
Wzorzec do usuwania obiektu, nazywany [wzorcem usuwania](../../../docs/standard/design-guidelines/dispose-pattern.md), nakłada kolejność na okres istnienia obiektu. Wzorzec usuwania jest używany tylko w przypadku obiektów uzyskujących dostęp do niezarządzanych zasobów, takich jak dojścia do plików i potoków, dojścia do rejestru, dojścia oczekiwania lub wskaźniki do bloków w niezarządzanej pamięci. Z tego powodu moduł odśmiecania pamięci jest bardzo skuteczny w odzyskiwaniu nieużywanych zarządzanych obiektów, ale nie jest w stanie odzyskiwać niezarządzanych obiektów.  
  
Wzorzec usuwania ma dwa warianty:  
  
- Każdy zasób niezarządzany, który jest wykorzystywany przez typ, jest zawijany w bezpiecznym obsłudze (czyli <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>w klasie pochodnej z). W takim przypadku należy zaimplementować <xref:System.IDisposable> interfejs i dodatkową `Dispose(Boolean)` metodę. Jest to zalecana odmiana i nie wymaga przesłaniania <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.  
  
  > [!NOTE]
  > Przestrzeń nazw zawiera zestaw klas <xref:System.Runtime.InteropServices.SafeHandle>pochodnych, które są wymienione w sekcji [using Safe Handles.](#SafeHandles) <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Jeśli nie możesz znaleźć klasy, która jest odpowiednia do zwolnienia niezarządzanego zasobu, można zaimplementować własną podklasę <xref:System.Runtime.InteropServices.SafeHandle>.  
  
- Implementujesz <xref:System.IDisposable> interfejs i metodę dodatkową `Dispose(Boolean)` , <xref:System.Object.Finalize%2A?displayProperty=nameWithType> a także zastąpisz metodę. Należy przesłonić <xref:System.Object.Finalize%2A> , aby upewnić się, że niezarządzane <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> zasoby zostaną usunięte, jeśli implementacja nie zostanie wywołana przez odbiorcę typu. Jeśli używasz zalecanej techniki omówionej w poprzednim wypunktowaniu, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> Klasa robi to w Twoim imieniu.  
  
Aby zapewnić, że zasoby są zawsze odpowiednio czyszczone, <xref:System.IDisposable.Dispose%2A> Metoda powinna być wywoływana wiele razy bez zgłaszania wyjątku.  
  
Przykład kodu dla <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metody pokazuje, jak agresywne wyrzucanie elementów bezużytecznych może spowodować, że finalizator jest uruchamiany, gdy członek odzyskiwanego obiektu jest nadal wykonywany. Dobrym pomysłem jest wywołanie <xref:System.GC.KeepAlive%2A> metody na końcu <xref:System.IDisposable.Dispose%2A> długotrwałej metody.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Metoda Dispose() a metoda Dispose(Boolean)  

Interfejs wymaga implementacji pojedynczej <xref:System.IDisposable.Dispose%2A>metody bez parametrów. <xref:System.IDisposable> Jednak wzorzec Dispose wymaga zastosowania dwóch `Dispose` metod:  
  
- Publiczna implementacja niewirtualna (`NonInheritable` w Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , która nie ma parametrów.  
  
- Chroniona wirtualna (`Overridable` w Visual Basic) `Dispose` Metoda, której sygnatura:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Przeciążenie metody Dispose ()

Ponieważ publiczne, niewirtualne (`NonInheritable` w Visual Basic), `Dispose` Metoda bez parametrów jest wywoływana przez odbiorcę typu, jego celem jest zwolnienie niezarządzanych zasobów i wskazanie, że finalizator, jeśli taki istnieje, nie musi być uruchamiany. Z tego powodu ma standardową implementację:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda wykonuje wszystkie operacje czyszczenia obiektów, dlatego Moduł wyrzucania elementów bezużytecznych nie musi już <xref:System.Object.Finalize%2A?displayProperty=nameWithType> wywoływać przesłonięcia obiektów. `Dispose` W związku z tym wywołanie <xref:System.GC.SuppressFinalize%2A> metody uniemożliwia uruchomienie finalizatora przez moduł wyrzucania elementów bezużytecznych. Jeśli typ nie ma finalizatora, wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nie ma żadnego wpływu. Należy pamiętać, że rzeczywista część zwalniania niezarządzanych zasobów jest wykonywana przez drugie Przeciążenie `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Przeciążenie metody Dispose (Boolean)

W drugim przeciążeniu parametr Dispose ma wartość <xref:System.Boolean> wskazującą, czy <xref:System.IDisposable.Dispose%2A> wywołanie metody pochodzi z metody (jej wartość jest `true`) czy z finalizatora (jego wartość to `false`).  
  
Treść metody składa się z dwóch bloków kodu:  
  
- Blok zwalniający niezarządzane zasoby. Ten blok jest wykonywany niezależnie od wartości `disposing` parametru.  
  
- Blok warunkowy zwalniający zarządzane zasoby. Ten blok jest wykonywany, gdy wartość `disposing` jest `true`. Zarządzane zasoby, które zwalnia, to m.in.:  
  
  **Obiekty zarządzane, które <xref:System.IDisposable>implementują.** Bloku warunkowego można użyć do wywołania ich <xref:System.IDisposable.Dispose%2A> implementacji. Jeśli użyto bezpiecznego dojścia do zawijania niezarządzanego zasobu, należy wywołać <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementację tutaj.  
  
  **Zarządzane obiekty, które zużywają duże ilości pamięci lub zużywają niewystarczające zasoby.** Bezpośrednie zwalnianie tych obiektów w `Dispose` metodzie zwalnia je szybciej niż gdyby były odzyskiwane niedeterministycznie przez moduł wyrzucania elementów bezużytecznych.  
  
Jeśli wywołanie metody pochodzi od finalizatora (to oznacza, że w przypadku likwidacji `false`jest), zostanie wykonany tylko kod, który zwolni niezarządzane zasoby. Ponieważ kolejność, w której moduł zbierający elementy bezużyteczne niszczy obiekty zarządzane podczas finalizowania, nie jest zdefiniowana `Dispose` , wywołanie tego przeciążenia z `false` wartością zapobiega próbie zwolnienia zarządzanych zasobów, które mogą mieć zostało już przywrócone.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementowanie wzorca usuwania dla klasy bazowej

Podczas implementowania wzorca usuwania dla klasy bazowej należy dostarczyć następujące elementy:  
  
> [!IMPORTANT]
> Należy zaimplementować ten wzorzec dla wszystkich klas bazowych, które <xref:System.IDisposable.Dispose> implementują i `sealed` nie`NotInheritable` są (w Visual Basic).  
  
- Implementacja, która `Dispose(Boolean)` wywołuje metodę. <xref:System.IDisposable.Dispose%2A>  
  
- `Dispose(Boolean)` Metoda, która wykonuje rzeczywistą część zwalniania zasobów.  
  
- Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle> , która otacza niezarządzany zasób (zalecane) lub przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasa zawiera finalizator, który uwalnia Cię do kodu.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która używa bezpiecznego dojścia.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu do zilustrowania wzorca; zamiast tego można użyć dowolnego obiektu <xref:System.Runtime.InteropServices.SafeHandle> pochodnego. Należy zauważyć, że przykład nie tworzy prawidłowo wystąpienia <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> W C#programie przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> przez zdefiniowanie [destruktora](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasa pochodna klasy, która implementuje <xref:System.IDisposable> interfejs, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> nie należy implementować <xref:System.IDisposable>, ponieważ Implementacja klasy bazowej jest dziedziczona przez klasy pochodne. Tak więc, aby zaimplementować wzorzec usuwania dla klasy pochodnej, należy dostarczyć następujące elementy:  
  
- `protected Dispose(Boolean)` Metoda, która zastępuje metodę klasy bazowej i wykonuje rzeczywistą liczbę zasobów klasy pochodnej. Ta metoda powinna również wywołać `Dispose(Boolean)` metodę klasy bazowej i przekazać jej stan likwidacji dla tego argumentu.  
  
- Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle> , która otacza niezarządzany zasób (zalecane) lub przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasa zawiera finalizator, który uwalnia Cię do kodu. W przypadku zapewnienia finalizatora należy wywołać `Dispose(Boolean)` Przeciążenie przy użyciu argumentu `false`usuwania.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu do zilustrowania wzorca; zamiast tego można użyć dowolnego obiektu <xref:System.Runtime.InteropServices.SafeHandle> pochodnego. Należy zauważyć, że przykład nie tworzy prawidłowo wystąpienia <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy pochodnej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> W C#programie przesłonięcie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> przez zdefiniowanie [destruktora](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Używanie bezpiecznych dojść

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. Dlatego zalecamy konstruowanie <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> obiektów zamiast implementowania finalizatora.  
  
Klasy pochodne <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy upraszczają problemy z okresem istnienia obiektów przez przypisanie i zwolnienie dojść bez przeszkód. Zawierają finalizator krytyczny, który gwarantuje działanie w trakcie zwalniania domeny aplikacji. Aby uzyskać więcej informacji na temat korzyści z używania bezpiecznego dojścia, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>Zobacz. Następujące klasy pochodne w <xref:Microsoft.Win32.SafeHandles> przestrzeni nazw zapewniają bezpieczne dojścia:  
  
- Klasy <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, i<xref:Microsoft.Win32.SafeHandles.SafePipeHandle> , dla plików, plików mapowanych na pamięć i potoków.  
  
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Klasa dla widoków pamięci.  
  
- Klasy <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> i<xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> , dla konstrukcji kryptografii.  
  
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Klasa dla kluczy rejestru.  
  
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Klasa, dla uchwytów oczekiwania.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy bazowej

Poniższy przykład ilustruje wzorzec Dispose dla klasy bazowej, `DisposableStreamResource`który używa bezpiecznego dojścia do hermetyzowania niezarządzanych zasobów. Definiuje `DisposableResource` klasę, która <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> używa do zawijania <xref:System.IO.Stream> obiektu, który reprezentuje otwarty plik. Metoda zawiera również pojedynczą `Size`właściwość, która zwraca łączną liczbę bajtów w strumieniu pliku. `DisposableResource`  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy pochodnej

Poniższy przykład ilustruje wzorzec usuwania dla klasy `DisposableStreamResource2`pochodnej, która dziedziczy `DisposableStreamResource` z klasy przedstawionej w poprzednim przykładzie. Klasa dodaje dodatkową metodę, `WriteFileInfo`i <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> używa obiektu do zawijania uchwytu zapisywalnego pliku.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Instrukcje: definiowanie oraz stosowanie klas i struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Wzorzec Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md)
