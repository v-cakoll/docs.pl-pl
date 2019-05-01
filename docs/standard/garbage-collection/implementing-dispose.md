---
title: Implementacja metody Dispose
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
ms.openlocfilehash: 683a71b27d3e3dd1c0db4e49c2c188ccad0fb6d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965233"
---
# <a name="implementing-a-dispose-method"></a>Implementacja metody Dispose

Możesz wdrożyć <xref:System.IDisposable.Dispose%2A> metodę, aby zwolnić zasoby niezarządzane używane przez aplikację. Moduł zbierający elementy bezużyteczne .NET nie alokacji lub zwolnienia niezarządzanej pamięci.  
  
Wzorzec usuwania obiektu, nazywany [wzorca usuwania](../../../docs/standard/design-guidelines/dispose-pattern.md), nakłada zamówienie na okres istnienia obiektu. Wzorzec usuwania jest używany tylko w przypadku obiektów uzyskujących dostęp do niezarządzanych zasobów, takich jak dojścia do plików i potoków, dojścia do rejestru, dojścia oczekiwania lub wskaźniki do bloków w niezarządzanej pamięci. Z tego powodu moduł odśmiecania pamięci jest bardzo skuteczny w odzyskiwaniu nieużywanych zarządzanych obiektów, ale nie jest w stanie odzyskiwać niezarządzanych obiektów.  
  
Wzorzec usuwania ma dwa warianty:  
  
* OPAKOWYWANIE każdy niezarządzany zasób, którego używa typ, jest w bezpiecznym dojściu (czyli w klasie pochodnej od <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). W takim przypadku należy zaimplementować <xref:System.IDisposable> interfejsu i dodatkowego `Dispose(Boolean)` metody. To jest odmianą zalecany i nie wymaga zastępowania <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Udostępnia zestaw klas pochodzących od klasy <xref:System.Runtime.InteropServices.SafeHandle>, które są wymienione w [używanie bezpiecznych dojść](#SafeHandles) sekcji. Jeśli nie można odnaleźć klasy, która jest odpowiednia do zwalniania niezarządzany zasób, można zaimplementować własną podklasę klasy <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Możesz wdrożyć <xref:System.IDisposable> interfejsu i dodatkowego `Dispose(Boolean)` metody, a także Przesłoń <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Konieczne jest przesłonięcie <xref:System.Object.Finalize%2A> aby upewnić się, że niezarządzane zasoby będą usuwane, jeśli Twoja <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> wdrożenia nie jest wywoływana przez konsumenta danego typu. Jeśli używasz zalecanej techniki opisanej w poprzednim punkcie <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy dzieje w Twoim imieniu.  
  
Aby mieć pewność, że zasoby są zawsze odpowiednio czyszczone, <xref:System.IDisposable.Dispose%2A> metoda powinna być wywoływana wiele razy bez zgłoszenia wyjątku.  
  
Przykładowy kod podany dla <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metoda ma pokazać, jak agresywne wyrzucanie elementów bezużytecznych może powodować finalizator do uruchomienia, gdy członek odzyskiwanego obiektu nadal działa. To dobry pomysł, aby wywołać <xref:System.GC.KeepAlive%2A> metoda na końcu długiej <xref:System.IDisposable.Dispose%2A> metody.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Metoda Dispose() a metoda Dispose(Boolean)  

<xref:System.IDisposable> Interfejsu wymaga implementacji pojedynczej metody bez parametrów <xref:System.IDisposable.Dispose%2A>. Jednak wzorzec usuwania wymaga dwóch `Dispose` metody do zaimplementowania:  
  
* Publiczną niewirtualną (`NonInheritable` w języku Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację, która nie ma parametrów.  
  
* Chroniona, wirtualna (`Overridable` w języku Visual Basic) `Dispose` metodę, której sygnatura to:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Przeciążenie metody Dispose()

Ponieważ publiczną, niewirtualną (`NonInheritable` w języku Visual Basic), bez parametrów `Dispose` metoda jest wywoływana przez konsumenta typu, jej celem jest zwolnienie niezarządzanych zasobów i, aby wskazać, że finalizator, jeśli jest obecna, nie musi zostać uruchomiony. Z tego powodu ma standardową implementację:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` Metoda wykonuje wszystkie Oczyszczanie obiektu, więc moduł odśmiecania pamięci nie musi już wywoływać <xref:System.Object.Finalize%2A?displayProperty=nameWithType> zastąpienia. W związku z tym, wywołanie <xref:System.GC.SuppressFinalize%2A> metoda uniemożliwia uruchomienie finalizatora moduł odśmiecania pamięci. Jeśli typ nie ma finalizatora, wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nie ma wpływu. Należy pamiętać, że rzeczywista praca przy zwalnianiu niezarządzanych zasobów jest wykonywana przez drugie przeciążenie `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Przeciążenie Dispose(Boolean)

W drugie przeciążenie *disposing* parametr jest <xref:System.Boolean> oznacza to, czy wywołanie metody pochodzi z <xref:System.IDisposable.Dispose%2A> — metoda (jego wartość wynosi `true`) czy z finalizatora (jego wartość wynosi `false`).  
  
Treść metody składa się z dwóch bloków kodu:  
  
* Blok zwalniający niezarządzane zasoby. Ten blok jest wykonywany niezależnie od wartości `disposing` parametru.  
  
* Blok warunkowy zwalniający zarządzane zasoby. Ten blok jest wykonywany, jeśli wartość `disposing` jest `true`. Zarządzane zasoby, które zwalnia, to m.in.:  
  
  **Zarządzane obiekty, które implementują <xref:System.IDisposable>.** Bloku warunkowego może służyć do wywołania ich <xref:System.IDisposable.Dispose%2A> implementacji. Jeśli używano bezpiecznego dojścia do niezarządzanego zasobu w otoce, należy wywołać <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> tutaj implementację.  
  
  **Zarządzane obiekty, które zużywają duże ilości pamięci lub zużywają deficytowe zasoby.** Zwolnienie tych obiektów jawnie w `Dispose` metoda zwalnia je szybciej niż w przypadku ich były odzyskiwane niedeterministycznie przez moduł odśmiecania pamięci.  
  
Jeśli wywołanie metody pochodzi z finalizatora (to znaczy, jeśli *disposing* jest `false`), jest wykonywany tylko kod zwalniający niezarządzane zasoby. Ponieważ nie określono kolejności, w jakiej moduł odśmiecania pamięci niszczy zarządzane obiekty podczas finalizacji, wywołujące ten element `Dispose` przeciążenia z wartością `false` uniemożliwia to finalizatorowi podjęcie próby zwolnienie zarządzanych zasobów, które mogą mieć już odzyskane.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementowanie wzorca usuwania dla klasy bazowej

Podczas implementowania wzorca usuwania dla klasy bazowej należy dostarczyć następujące elementy:  
  
> [!IMPORTANT]
> Należy zaimplementować ten wzorzec dla wszystkich klas bazowych, które implementują <xref:System.IDisposable.Dispose> i nie są `sealed` (`NotInheritable` w języku Visual Basic).  
  
* A <xref:System.IDisposable.Dispose%2A> implementację, która wywołuje `Dispose(Boolean)` metody.  
  
* A `Dispose(Boolean)` metodę, która wykonuje rzeczywistą pracę przy zwalnianiu zasobów.  
  
* Klasa pochodząca z <xref:System.Runtime.InteropServices.SafeHandle> która umieszcza niezarządzany zasób w otoce (zalecane) lub zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasy dostarcza finalizator, dzięki czemu kodu finalizatora.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy bazowej, w którym jest używane bezpieczne dojście.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu w celu zilustrowania wzorca; każdy obiekt jest pochodną <xref:System.Runtime.InteropServices.SafeHandle> można także użyć. Należy zauważyć, że przykład prawidłowo tworzy wystąpienia jego <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy bazowej, w którym jest zastępowana <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> W języku C#, możesz zastąpić <xref:System.Object.Finalize%2A?displayProperty=nameWithType> , definiując [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasa pochodząca z klasy, która implementuje <xref:System.IDisposable> nie powinna implementować interfejsu <xref:System.IDisposable>, ponieważ Implementacja klasy bazowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jest dziedziczona przez jej klas pochodnych. Tak więc, aby zaimplementować wzorzec usuwania dla klasy pochodnej, należy dostarczyć następujące elementy:  
  
* A `protected Dispose(Boolean)` metodę, która zastępuje metodę klasy bazowej i wykonuje rzeczywistą pracę przy zwalnianiu zasobów klasy pochodnej. Ta metoda powinna także wywoływać `Dispose(Boolean)` metody podstawowej klasy, a następnie przekaż jego stan operacji Dispose dla argumentu.  
  
* Klasa pochodząca z <xref:System.Runtime.InteropServices.SafeHandle> która umieszcza niezarządzany zasób w otoce (zalecane) lub zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasy dostarcza finalizator, dzięki czemu kodu finalizatora. Jeśli podasz finalizator, powinien wywoływać `Dispose(Boolean)` przeciążenia z *disposing* argument `false`.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu w celu zilustrowania wzorca; każdy obiekt jest pochodną <xref:System.Runtime.InteropServices.SafeHandle> można także użyć. Należy zauważyć, że przykład prawidłowo tworzy wystąpienia jego <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, która zastępuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> W języku C#, możesz zastąpić <xref:System.Object.Finalize%2A?displayProperty=nameWithType> , definiując [destruktor](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Używanie bezpiecznych dojść

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. Dlatego zalecamy konstruowanie <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> obiektów, a nie Implementowanie finalizatorów.  
  
Klasy pochodne <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasa upraszcza kwestie istnienia obiektu i zwalniają dojścia bez zakłóceń. Zawierają finalizator krytyczny, który gwarantuje działanie w trakcie zwalniania domeny aplikacji. Aby uzyskać więcej informacji o zaletach używania bezpiecznego dojścia, zobacz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Następujące klasy pochodne w <xref:Microsoft.Win32.SafeHandles> przestrzeni nazw oferują bezpieczne dojścia:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, I <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> klasy, plików, plików zamapowanych w pamięci oraz potoków.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Klasy widoków pamięci.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, I <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> klasy konstrukcji kryptograficznych.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Klasy dla kluczy rejestru.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Klasy dojść oczekiwania.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy bazowej

Poniższy przykład ilustruje wzorca usuwania dla klasy bazowej, `DisposableStreamResource`, że używa bezpiecznego dojścia w celu hermetyzowania niezarządzanych zasobów. Definiuje on `DisposableResource` klasy, która używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> opakowywać <xref:System.IO.Stream> obiekt, który reprezentuje otwartego pliku. `DisposableResource` Metoda obejmuje także jedną właściwość `Size`, która zwraca wartość całkowita liczba bajtów w strumieniu plików.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy pochodnej

Poniższy przykład ilustruje wzorca usuwania dla klasy pochodnej `DisposableStreamResource2`, która dziedziczy z `DisposableStreamResource` klasy przedstawiony w poprzednim przykładzie. Ta klasa dodaje kolejną metodę `WriteFileInfo`i wykorzystuje <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu w otoce dojścia do zapisywalnego pliku.  
  
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
