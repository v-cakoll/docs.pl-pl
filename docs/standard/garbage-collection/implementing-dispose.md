---
title: Implementowanie disposeu metody
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: f3d3269ccf56954f963762503d2bc1c53b9e6b83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78238991"
---
# <a name="implementing-a-dispose-method"></a>Implementowanie disposeu metody

Zaimplementować <xref:System.IDisposable.Dispose%2A> metodę do zwolnienia zasobów niezarządzanych używanych przez aplikację. Moduł zbierający elementy bezużyteczne .NET nie przydziela ani nie zwalnia pamięci niezarządzanej.  
  
Wzorzec do usuwania obiektu, określany jako [wzorzec utylizacji,](implementing-dispose.md)nakłada porządek na okres istnienia obiektu. Wzorzec usuwania jest używany tylko w przypadku obiektów uzyskujących dostęp do niezarządzanych zasobów, takich jak dojścia do plików i potoków, dojścia do rejestru, dojścia oczekiwania lub wskaźniki do bloków w niezarządzanej pamięci. Z tego powodu moduł odśmiecania pamięci jest bardzo skuteczny w odzyskiwaniu nieużywanych zarządzanych obiektów, ale nie jest w stanie odzyskiwać niezarządzanych obiektów.  
  
Wzorzec usuwania ma dwa warianty:  
  
- Zawijasię każdy zasób niezarządzany, który typ używa <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>w bezpiecznym dojściu (to jest w klasie pochodzącej z). W takim przypadku należy <xref:System.IDisposable> zaimplementować `Dispose(Boolean)` interfejs i dodatkową metodę. Jest to zalecana odmiana i nie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> wymaga zastępowania metody.  
  
  > [!NOTE]
  > Obszar <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> nazw zawiera zestaw klas pochodzących <xref:System.Runtime.InteropServices.SafeHandle>z , które są wymienione w [using safe dojścia](#SafeHandles) sekcji. Jeśli nie możesz znaleźć klasy, która nadaje się do zwolnienia zasobu niezarządzanego, możesz zaimplementować własną <xref:System.Runtime.InteropServices.SafeHandle>podklasę .  
  
- Zaimplementować <xref:System.IDisposable> interfejs i `Dispose(Boolean)` dodatkową metodę, a <xref:System.Object.Finalize%2A?displayProperty=nameWithType> także zastąpić metodę. Należy zastąpić, <xref:System.Object.Finalize%2A> aby upewnić się, że zasoby <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> niezarządzane są usuwane, jeśli implementacja nie jest wywoływana przez konsumenta typu. Jeśli używasz zalecanej techniki omówione w poprzednim <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> punktor, klasa robi to w Twoim imieniu.  
  
Aby upewnić się, że zasoby są <xref:System.IDisposable.Dispose%2A> zawsze czyszczone odpowiednio, metoda powinna być wywoływana wiele razy bez zgłaszania wyjątku.  
  
Przykład kodu przewidziany <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> dla metody pokazuje, jak wyrzucanie elementów bezużytecznych może spowodować uruchomienie finalizatora, podczas gdy niezarządzane odwołanie do obiektu lub jego członków jest nadal używane. Może to mieć sens, <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> aby użyć do obiektu nie kwalifikują się do wyrzucania elementów bezużytecznych od początku bieżącej procedury do punktu, w którym ta metoda jest wywoływana.
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Metoda Dispose() a metoda Dispose(Boolean)  

Interfejs <xref:System.IDisposable> wymaga implementacji pojedynczej metody <xref:System.IDisposable.Dispose%2A>bezparametrowej, . Jednak wzorzec `Dispose` utylizacji wymaga dwóch metod do zaimplementowania:  
  
- Publiczna implementacja niewirtualna (w`NonInheritable` języku Visual Basic), <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> która nie ma parametrów.  
  
- Chroniona`Overridable` metoda wirtualna `Dispose` (w języku Visual Basic), której podpis jest:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Przeciążenie Dispose()

Ponieważ publiczne, niewirtualne`NonInheritable` (w języku `Dispose` Visual Basic), metoda bezparametrów jest wywoływana przez konsumenta typu, jego celem jest zwolnić zasoby niezarządzane i wskazać, że finalizator, jeśli jest obecny, nie musi działać. Z tego powodu ma standardową implementację:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Metoda `Dispose` wykonuje wszystkie oczyszczania obiektu, więc moduł zbierający elementy bezużyteczne <xref:System.Object.Finalize%2A?displayProperty=nameWithType> nie musi już wywoływać zastąpienia obiektów. W związku z <xref:System.GC.SuppressFinalize%2A> tym wywołanie metody uniemożliwia moduł zbierający elementy bezużyteczne z uruchomieniem finalizatora. Jeśli typ nie ma finalizatora, wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nie ma wpływu. Należy zauważyć, że rzeczywista praca zwalniania zasobów niezarządzanych `Dispose` jest wykonywana przez drugie przeciążenie metody.  
  
### <a name="the-disposeboolean-overload"></a>Przeciążenie Dispose(logiczne)

W drugim przeciążeniu, usuwanie parametr *disposing* <xref:System.Boolean> jest, który wskazuje, czy <xref:System.IDisposable.Dispose%2A> wywołanie metody `true`pochodzi z metody (jego `false`wartość jest ) lub z finalizatora (jego wartość jest ).  
  
Treść metody składa się z dwóch bloków kodu:  
  
- Blok zwalniający niezarządzane zasoby. Ten blok jest wykonywany niezależnie `disposing` od wartości parametru.  
  
- Blok warunkowy zwalniający zarządzane zasoby. Ten blok jest wykonywany, jeśli wartość `disposing` jest `true`. Zarządzane zasoby, które zwalnia, to m.in.:  
  
  **Obiekty zarządzane, <xref:System.IDisposable>które implementują .** Blok warunkowy może służyć <xref:System.IDisposable.Dispose%2A> do wywoływania ich implementacji. Jeśli używasz bezpiecznego dojścia do zawijania zasobu niezarządzanego, należy wywołać implementację <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> w tym miejscu.  
  
  **Zarządzane obiekty, które zużywają duże ilości pamięci lub zużywają ograniczone zasoby.** Zwalnianie tych obiektów jawnie w `Dispose` metodzie zwalnia je szybciej niż gdyby zostały odzyskane nie deterministycznie przez moduł zbierający elementy bezużyteczne.  
  
Jeśli wywołanie metody pochodzi z finalizatora (oznacza `false`to, jeśli jest *usuwanie* jest ), tylko kod, który zwalnia zasoby niezarządzane wykonuje. Ponieważ kolejność, w której moduł zbierający elementy bezużyteczne niszczy obiekty `Dispose` zarządzane podczas finalizacji `false` nie jest zdefiniowana, wywołanie tego przeciążenia z wartością uniemożliwia finalizatorowi próbę zwolnienia zarządzanych zasobów, które mogły już zostać odzyskane.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementowanie wzorca usuwania dla klasy bazowej

Podczas implementowania wzorca usuwania dla klasy bazowej należy dostarczyć następujące elementy:  
  
> [!IMPORTANT]
> Należy zaimplementować ten wzorzec dla `sealed` `NotInheritable` wszystkich klas podstawowych, które implementują <xref:System.IDisposable.Dispose> i nie są ( w języku Visual Basic).  
  
- Implementacja, <xref:System.IDisposable.Dispose%2A> która `Dispose(Boolean)` wywołuje metodę.  
  
- Metoda, `Dispose(Boolean)` która wykonuje rzeczywistą pracę zwalniania zasobów.  
  
- Klasa pochodząca z <xref:System.Runtime.InteropServices.SafeHandle> tego zawija zasób niezarządzany <xref:System.Object.Finalize%2A?displayProperty=nameWithType> (zalecane) lub zastąpienie metody. Klasa <xref:System.Runtime.InteropServices.SafeHandle> zapewnia finalizator, który zwalnia cię z konieczności kod jednego.  
  
Oto ogólny wzorzec do implementowania wzorca dispose dla klasy podstawowej, która używa bezpiecznego dojścia.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> W poprzednim przykładzie <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> użyto obiektu do zilustrowania wzorca; zamiast tego <xref:System.Runtime.InteropServices.SafeHandle> można użyć dowolnego obiektu pochodzącego. Należy zauważyć, że przykład nie poprawnie <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> utworzyć wystąpienia jego obiektu.  
  
Oto ogólny wzorzec do implementowania wzorca <xref:System.Object.Finalize%2A?displayProperty=nameWithType>dispose dla klasy podstawowej, która zastępuje .  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> W języku C#można zastąpić, <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definiując [destruktor](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasa pochodząca z klasy, która <xref:System.IDisposable> implementuje interfejs <xref:System.IDisposable>nie powinien implementować <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , ponieważ implementacja klasy podstawowej jest dziedziczona przez jego klas pochodnych. Zamiast tego, aby zwolnić zasoby klasy pochodnej, należy podać następujące elementy:  
  
- Metoda, `protected Dispose(Boolean)` która zastępuje metodę klasy podstawowej i wykonuje rzeczywistą pracę zwalniania zasobów klasy pochodnej. Ta metoda powinna `Dispose(Boolean)` również wywołać metodę klasy podstawowej i przekazać jej stan usuwania dla argumentu.  
  
- Klasa pochodząca z <xref:System.Runtime.InteropServices.SafeHandle> tego zawija zasób niezarządzany <xref:System.Object.Finalize%2A?displayProperty=nameWithType> (zalecane) lub zastąpienie metody. Klasa <xref:System.Runtime.InteropServices.SafeHandle> zapewnia finalizator, który zwalnia cię z konieczności kod jednego. Jeśli podasz finalizator, należy `Dispose(Boolean)` wywołać przeciążenie z `false`argumentem *usuwania* .  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> W poprzednim przykładzie <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> użyto obiektu do zilustrowania wzorca; zamiast tego <xref:System.Runtime.InteropServices.SafeHandle> można użyć dowolnego obiektu pochodzącego. Należy zauważyć, że przykład nie poprawnie <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> utworzyć wystąpienia jego obiektu.  
  
Oto ogólny wzorzec do implementowania wzorca dispose <xref:System.Object.Finalize%2A?displayProperty=nameWithType>dla klasy pochodnej, która zastępuje:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> W języku C#można zastąpić, <xref:System.Object.Finalize%2A?displayProperty=nameWithType> definiując [destruktor](../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>
## <a name="using-safe-handles"></a>Używanie bezpiecznych dojść

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. W związku z tym <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> zaleca się konstruowanie obiektów zamiast implementowania finalizatora.  
  
Klasy pochodzące z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy upraszczają problemy z okresem istnienia obiektu, przypisując i zwalniając uchwyty bez przerw. Zawierają finalizator krytyczny, który gwarantuje działanie w trakcie zwalniania domeny aplikacji. Aby uzyskać więcej informacji na temat zalet <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>korzystania z bezpiecznego uchwytu, zobacz . Następujące klasy pochodne <xref:Microsoft.Win32.SafeHandles> w obszarze nazw zapewniają bezpieczne dojścia:  
  
- , <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>i <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> klasa , dla plików, pamięci mapowane pliki i potoki.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> dla widoków pamięci.  
  
- , <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>i <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> klasy dla konstrukcji kryptografii.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> dla kluczy rejestru.  
  
- Klasa <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> dla uchwytów oczekiwania.  
  
<a name="base"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy bazowej

W poniższym przykładzie przedstawiono wzorzec `DisposableStreamResource`usuwania dla klasy podstawowej, który używa bezpiecznego dojścia do hermetyzacji zasobów niezarządzanych. Definiuje `DisposableResource` klasę, która używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> do <xref:System.IO.Stream> zawijania obiektu, który reprezentuje otwarty plik. Metoda `DisposableResource` zawiera również pojedynczą `Size`właściwość, która zwraca całkowitą liczbę bajtów w strumieniu plików.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy pochodnej

W poniższym przykładzie przedstawiono wzorzec `DisposableStreamResource2`dispose dla klasy `DisposableStreamResource` pochodnej, która dziedziczy po klasie przedstawionej w poprzednim przykładzie. Klasa dodaje dodatkową `WriteFileInfo`metodę i <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> używa obiektu do zawijania uchwytu zapisywalny plik.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Porady: definiowanie oraz stosowanie klas i struktur (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Wzorzec Dispose](implementing-dispose.md)
