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
ms.openlocfilehash: 8a29584dd5ed47ad1e8a336a7283cba9271f3abd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121211"
---
# <a name="implementing-a-dispose-method"></a>Implementowanie metody Dispose

Zaimplementuj metodę <xref:System.IDisposable.Dispose%2A>, aby zwolnić niezarządzane zasoby używane przez aplikację. Moduł wyrzucania elementów bezużytecznych platformy .NET nie przydziela lub nie zwalnia pamięci niezarządzanej.  
  
Wzorzec do usuwania obiektu, nazywany [wzorcem usuwania](../../../docs/standard/design-guidelines/dispose-pattern.md), nakłada kolejność na okres istnienia obiektu. Wzorzec usuwania jest używany tylko w przypadku obiektów uzyskujących dostęp do niezarządzanych zasobów, takich jak dojścia do plików i potoków, dojścia do rejestru, dojścia oczekiwania lub wskaźniki do bloków w niezarządzanej pamięci. Z tego powodu moduł odśmiecania pamięci jest bardzo skuteczny w odzyskiwaniu nieużywanych zarządzanych obiektów, ale nie jest w stanie odzyskiwać niezarządzanych obiektów.  
  
Wzorzec usuwania ma dwa warianty:  
  
- Każdy zasób niezarządzany, który jest wykorzystywany przez typ, jest zawijany w bezpiecznym obsłudze (czyli w klasie pochodnej <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). W takim przypadku należy zaimplementować interfejs <xref:System.IDisposable> i dodatkową metodę `Dispose(Boolean)`. Jest to zalecana odmiana i nie wymaga zastąpienia metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
  > [!NOTE]
  > Przestrzeń nazw <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> zawiera zestaw klas pochodnych od <xref:System.Runtime.InteropServices.SafeHandle>, które są wymienione w sekcji [using Safe Handles](#SafeHandles) . Jeśli nie możesz znaleźć klasy, która jest odpowiednia do zwolnienia niezarządzanego zasobu, można zaimplementować własną podklasę <xref:System.Runtime.InteropServices.SafeHandle>.  
  
- Implementujesz interfejs <xref:System.IDisposable> i dodatkową metodę `Dispose(Boolean)`, a także zastąpisz metodę <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Należy zastąpić <xref:System.Object.Finalize%2A>, aby upewnić się, że niezarządzane zasoby są usuwane, jeśli <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacja nie zostanie wywołana przez odbiorcę typu. Jeśli używasz zalecanej techniki omówionej w poprzednim wypunktowaniu, Klasa <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> robi to w Twoim imieniu.  
  
Aby zapewnić, że zasoby są zawsze odpowiednio czyszczone, Metoda <xref:System.IDisposable.Dispose%2A> powinna być wywoływana wiele razy bez zgłaszania wyjątku.  
  
Przykład kodu podany dla metody <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> pokazuje, jak agresywne wyrzucanie elementów bezużytecznych może spowodować uruchomienie finalizatora w czasie, gdy element członkowski odzyskiwanego obiektu jest nadal wykonywany. Dobrym pomysłem jest wywołanie metody <xref:System.GC.KeepAlive%2A> na końcu długiej <xref:System.IDisposable.Dispose%2A>ej metody.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Metoda Dispose() a metoda Dispose(Boolean)  

Interfejs <xref:System.IDisposable> wymaga implementacji pojedynczej metody bez parametrów, <xref:System.IDisposable.Dispose%2A>. Jednak wzorzec Dispose wymaga zaimplementowania dwóch metod `Dispose`:  
  
- Publiczna, niewirtualna (`NonInheritable` w Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacja, która nie ma parametrów.  
  
- Chroniona wirtualna (`Overridable` w Visual Basic) `Dispose` Metoda, której podpis to:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Przeciążenie metody Dispose ()

Ze względu na to, że publiczna, niewirtualna (`NonInheritable` w Visual Basic) Metoda `Dispose` bezparametrowa jest wywoływana przez odbiorcę typu, jego celem jest zwolnienie niezarządzanych zasobów i wskazanie, że finalizator, jeśli taki istnieje, nie musi być uruchamiany. Z tego powodu ma standardową implementację:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda `Dispose` wykonuje wszystkie operacje czyszczenia obiektów, dlatego Moduł wyrzucania elementów bezużytecznych nie musi już wywoływać obiektów <xref:System.Object.Finalize%2A?displayProperty=nameWithType> zastąpień. W związku z tym wywołanie metody <xref:System.GC.SuppressFinalize%2A> uniemożliwia uruchomienie finalizatora przez moduł wyrzucania elementów bezużytecznych. Jeśli typ nie ma finalizatora, wywołanie do <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nie ma wpływu. Należy pamiętać, że rzeczywista część zwalniania niezarządzanych zasobów jest wykonywana przez drugie Przeciążenie metody `Dispose`.  
  
### <a name="the-disposeboolean-overload"></a>Przeciążenie metody Dispose (Boolean)

W drugim przeciążeniu parametr *Dispose* jest <xref:System.Boolean>, który wskazuje, czy wywołanie metody pochodzi z metody <xref:System.IDisposable.Dispose%2A> (jej wartość jest `true`) czy z finalizatora (jego wartość jest `false`).  
  
Treść metody składa się z dwóch bloków kodu:  
  
- Blok zwalniający niezarządzane zasoby. Ten blok jest wykonywany niezależnie od wartości parametru `disposing`.  
  
- Blok warunkowy zwalniający zarządzane zasoby. Ten blok jest wykonywany, gdy wartość `disposing` jest `true`. Zarządzane zasoby, które zwalnia, to m.in.:  
  
  **Zarządzane obiekty, które implementują <xref:System.IDisposable>.** Bloku warunkowego można użyć do wywołania ich implementacji <xref:System.IDisposable.Dispose%2A>. Jeśli użyto bezpiecznego dojścia do zawijania niezarządzanego zasobu, należy wywołać implementację <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> w tym miejscu.  
  
  **Zarządzane obiekty, które zużywają duże ilości pamięci lub zużywają niewystarczające zasoby.** Bezpośrednie zwalnianie tych obiektów w metodzie `Dispose` zwalnia je szybciej, niż gdyby były odzyskiwane niedeterministycznie przez moduł wyrzucania elementów bezużytecznych.  
  
Jeśli wywołanie metody pochodzi od finalizatora (to oznacza, *że jeśli zostanie* `false`, zostanie wykonany tylko kod, który zwolni niezarządzane zasoby. Ponieważ kolejność, w której moduł wyrzucania elementów bezużytecznych niszczy obiekty zarządzane podczas finalizowania, nie jest zdefiniowana, wywołanie tego `Dispose` Przeciążenie z wartością `false` uniemożliwia finalizatorowi podejmowanie prób zwolnienia zarządzanych zasobów, które mogły już zostać odzyskać.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementowanie wzorca usuwania dla klasy bazowej

Podczas implementowania wzorca usuwania dla klasy bazowej należy dostarczyć następujące elementy:  
  
> [!IMPORTANT]
> Należy zaimplementować ten wzorzec dla wszystkich klas bazowych, które implementują <xref:System.IDisposable.Dispose> i nie `sealed` (`NotInheritable` w Visual Basic).  
  
- Implementacja <xref:System.IDisposable.Dispose%2A>, która wywołuje metodę `Dispose(Boolean)`.  
  
- Metoda `Dispose(Boolean)`, która wykonuje rzeczywistą część zwalniania zasobów.  
  
- Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle>, która otacza zasób niezarządzany (zalecane) lub przesłonięcie metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Klasa <xref:System.Runtime.InteropServices.SafeHandle> zapewnia finalizator, który uwalnia Cię do kodu.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która używa bezpiecznego dojścia.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Poprzedni przykład używa obiektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do zilustrowania wzorca; Zamiast tego można użyć dowolnego obiektu pochodnego <xref:System.Runtime.InteropServices.SafeHandle>. Należy zauważyć, że przykład nie tworzy poprawnie wystąpienia obiektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy bazowej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> W C#programie zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> przez zdefiniowanie [destruktora](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasa pochodna klasy implementującej interfejs <xref:System.IDisposable> nie powinna implementować <xref:System.IDisposable>, ponieważ Implementacja klasy bazowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jest dziedziczona przez klasy pochodne. Tak więc, aby zaimplementować wzorzec usuwania dla klasy pochodnej, należy dostarczyć następujące elementy:  
  
- Metoda `protected Dispose(Boolean)`, która zastępuje metodę klasy bazowej i wykonuje rzeczywistą ilość pracy w celu zwolnienia zasobów klasy pochodnej. Ta metoda powinna również wywołać metodę `Dispose(Boolean)` klasy bazowej i przekazać jej stan likwidacji dla tego argumentu.  
  
- Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle>, która otacza zasób niezarządzany (zalecane) lub przesłonięcie metody <xref:System.Object.Finalize%2A?displayProperty=nameWithType>. Klasa <xref:System.Runtime.InteropServices.SafeHandle> zapewnia finalizator, który uwalnia Cię do kodu. W przypadku zapewnienia finalizatora należy wywołać Przeciążenie `Dispose(Boolean)` przy użyciu argumentu *usuwania* `false`.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Poprzedni przykład używa obiektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do zilustrowania wzorca; Zamiast tego można użyć dowolnego obiektu pochodnego <xref:System.Runtime.InteropServices.SafeHandle>. Należy zauważyć, że przykład nie tworzy poprawnie wystąpienia obiektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
Oto ogólny wzorzec implementowania wzorca usuwania dla klasy pochodnej, która zastąpi <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> W C#programie zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> przez zdefiniowanie [destruktora](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Używanie bezpiecznych dojść

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. W związku z tym zaleca się Konstruowanie obiektów <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> zamiast implementowania finalizatora.  
  
Klasy pochodne klasy <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> upraszczają problemy dotyczące okresu istnienia obiektów przez przypisanie i zwolnienie dojść bez przeszkód. Zawierają finalizator krytyczny, który gwarantuje działanie w trakcie zwalniania domeny aplikacji. Aby uzyskać więcej informacji na temat korzyści z używania bezpiecznego dojścia, zobacz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Następujące klasy pochodne w przestrzeni nazw <xref:Microsoft.Win32.SafeHandles> zapewniają bezpieczne dojścia:  
  
- Klasy <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>i <xref:Microsoft.Win32.SafeHandles.SafePipeHandle>, dla plików, plików mapowanych na pamięć i potoków.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>, dla widoków pamięci.  
  
- Klasy <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>i <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> dla konstrukcji kryptograficznych.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> dla kluczy rejestru.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>, dla uchwytów oczekiwania.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy bazowej

Poniższy przykład ilustruje wzorzec Dispose dla klasy bazowej, `DisposableStreamResource`, który używa bezpiecznego dojścia do hermetyzowania niezarządzanych zasobów. Definiuje klasę `DisposableResource`, która używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do otaczania <xref:System.IO.Stream> obiektu, który reprezentuje otwarty plik. Metoda `DisposableResource` zawiera również pojedynczą właściwość, `Size`, która zwraca łączną liczbę bajtów w strumieniu pliku.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy pochodnej

Poniższy przykład ilustruje wzorzec Dispose dla klasy pochodnej, `DisposableStreamResource2`, która dziedziczy z klasy `DisposableStreamResource` przedstawionej w poprzednim przykładzie. Klasa dodaje dodatkową metodę, `WriteFileInfo`i używa obiektu <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do zawijania uchwytu zapisywalnego pliku.  
  
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
