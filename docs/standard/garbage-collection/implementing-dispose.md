---
title: Implementacja metody Dispose
ms.custom: 
ms.date: 04/07/2017
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
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90edda252c33b6f07c795b8db1a0edaf1a688445
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-a-dispose-method"></a>Implementacja metody Dispose

Można zaimplementować <xref:System.IDisposable.Dispose%2A> metodę, aby zwolnić zasoby niezarządzane używane przez aplikację. Moduł zbierający elementy bezużyteczne .NET nie przydzielić lub wersji niezarządzanej pamięci.  
  
Wzorzec do likwidacji obiekt określany jako [wzorzec dispose](../../../docs/standard/design-guidelines/dispose-pattern.md), narzuca kolejności okresu istnienia obiektu. Wzorzec usuwania jest używany tylko w przypadku obiektów uzyskujących dostęp do niezarządzanych zasobów, takich jak dojścia do plików i potoków, dojścia do rejestru, dojścia oczekiwania lub wskaźniki do bloków w niezarządzanej pamięci. Z tego powodu moduł odśmiecania pamięci jest bardzo skuteczny w odzyskiwaniu nieużywanych zarządzanych obiektów, ale nie jest w stanie odzyskiwać niezarządzanych obiektów.  
  
Wzorzec usuwania ma dwa warianty:  
  
* Zawijaj każdego zasobu niezarządzanego korzystającej z typem w bezpieczne dojście (to znaczy w klasie pochodną <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). W takim przypadku wdrożenie <xref:System.IDisposable> interfejsu i dodatkowe `Dispose(Boolean)` metody. To jest zalecana zmiana i nie wymaga zastępowanie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Przestrzeń nazw zawiera zestaw klas pochodnych <xref:System.Runtime.InteropServices.SafeHandle>, które są wymienione w [przy użyciu bezpiecznego dojścia](#SafeHandles) sekcji. Jeśli nie można znaleźć klasy, która jest odpowiednia do zwalniania niezarządzanych zasobu, można zaimplementować własnych podklas <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Można zaimplementować <xref:System.IDisposable> interfejsu i dodatkowe `Dispose(Boolean)` metody, a także zastępować <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. Konieczne jest przesłonięcie <xref:System.Object.Finalize%2A> aby upewnić się, że zasoby niezarządzane są usuwane, jeśli Twoje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji nie jest wywoływany przez odbiorcę tego typu. Jeśli używasz zalecane techniki omówione w poprzedni punkt <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy robi to w Twoim imieniu.  
  
Pomaga zapewnić, że zasoby są zawsze wyczyścić odpowiednio, <xref:System.IDisposable.Dispose%2A> metody powinny móc wywoływać wielokrotnie bez generowania wyjątku.  
  
Przykładowy kod podany dla <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> metody pokazuje sposób agresywne pamięci kolekcji może spowodować finalizator do uruchomienia, gdy element członkowski obiektu regeneracji jest nadal wykonywane. Jest dobrym rozwiązaniem do wywołania <xref:System.GC.KeepAlive%2A> metody na końcu długich <xref:System.IDisposable.Dispose%2A> metody.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Metoda Dispose() a metoda Dispose(Boolean)  

<xref:System.IDisposable> Interfejsu wymaga wykonania jednej metody bez parametrów, <xref:System.IDisposable.Dispose%2A>. Jednak wzorzec dispose wymaga dwóch `Dispose` metody implementowane:  
  
* -Virtual publiczny (`NonInheritable` w języku Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację, która nie ma parametrów.  
  
* A chronione wirtualnych (`Overridable` w języku Visual Basic) `Dispose` metody, której sygnatura to:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Przeciążenie metody Dispose()

Ponieważ publicznego-wirtualna (`NonInheritable` w języku Visual Basic), bez parametrów `Dispose` metoda jest wywoływana przez odbiorcę tego typu, jej celem jest, aby zwolnić zasoby niezarządzane i aby wskazać, że finalizator, jeśli występuje, nie trzeba uruchamiać. Z tego powodu ma standardową implementację:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` — Metoda wykonuje czyszczenie wszystkich obiektów, dlatego moduł garbage collector już musi wywołać obiektów <xref:System.Object.Finalize%2A?displayProperty=nameWithType> zastąpienia. W związku z tym wywołaniu <xref:System.GC.SuppressFinalize%2A> metody uniemożliwia uruchomienie finalizatora przez moduł garbage collector. Jeśli typ nie ma żadnych finalizator wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> nie ma wpływu. Należy pamiętać, że faktyczną pracę zwalniania niezarządzanych zasobów jest wykonywane przez drugi przeciążenia `Dispose` metody.  
  
### <a name="the-disposeboolean-overload"></a>Przeciążenie Dispose(Boolean)

W drugim przeciążenia *disposing* parametr jest <xref:System.Boolean> wskazująca, czy wywołanie metody pochodzi z <xref:System.IDisposable.Dispose%2A> — metoda (jego wartość wynosi `true`) lub finalizatora (jego wartość wynosi `false`).  
  
Treść metody składa się z dwóch bloków kodu:  
  
* Blok zwalniający niezarządzane zasoby. Ten blok wykonuje niezależnie od wartości `disposing` parametru.  
  
* Blok warunkowy zwalniający zarządzane zasoby. Ten blok wykonuje, jeśli wartość `disposing` jest `true`. Zarządzane zasoby, które zwalnia, to m.in.:  
  
  **Zarządzane obiekty, które implementują <xref:System.IDisposable>.** Blok warunkowy może służyć do wywołania ich <xref:System.IDisposable.Dispose%2A> implementacji. Jeśli używasz bezpieczne dojście do opakowywania niezarządzanego zasobu, należy wywołać <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> implementację.  
  
  **Zarządzane obiekty, które używają duże ilości pamięci lub korzystać z ograniczonych zasobów.** Zwalnianie te obiekty jawnie w `Dispose` metoda zwalnia je szybciej niż w przypadku ich odzyskanych niejednoznaczne przez moduł garbage collector.  
  
Jeśli wywołanie metody pochodzi z finalizator (to znaczy, jeśli *disposing* jest `false`), wykonuje tylko kod zwalnia zasoby niezarządzane. Ponieważ nie określono kolejności, w której moduł zbierający elementy bezużyteczne niszczy podczas finalizacji zarządzanych obiektów, to wywołanie `Dispose` przeciążenia o wartości `false` uniemożliwia próby zwolnienia zarządzanych zasobów, które mogą mieć finalizator już została odzyskana.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implementowanie wzorca usuwania dla klasy bazowej

Podczas implementowania wzorca usuwania dla klasy bazowej należy dostarczyć następujące elementy:  
  
> [!IMPORTANT]
> Należy zaimplementować tego wzorca dla wszystkich klas podstawowych, które implementują <xref:System.IDisposable.Dispose> i nie są `sealed` (`NotInheritable` w języku Visual Basic).  
  
* A <xref:System.IDisposable.Dispose%2A> wdrożenia, który wywołuje `Dispose(Boolean)` metody.  
  
* A `Dispose(Boolean)` metodę, która wykonuje faktyczną pracę zwolnienia zasobów.  
  
* Każda klasa pochodzi od <xref:System.Runtime.InteropServices.SafeHandle> który opakowuje niezarządzanego zasobu (zalecane) lub zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasa udostępnia finalizatorze zwalnia z konieczności kodu.  
  
Poniżej przedstawiono ogólne wzorca w zakresie implementacji wzorca dispose dla klasy podstawowej, która używa bezpieczne dojście.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu w celu zilustrowania wzorzec; dowolny obiekt pochodną <xref:System.Runtime.InteropServices.SafeHandle> może być użyty. Należy pamiętać, że przykładzie nie prawidłowo utworzyć wystąpienia jego <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Poniżej przedstawiono ogólne wzorca w zakresie implementacji wzorca dispose dla klasy podstawowej, która zastępuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> W języku C#, Zastąp <xref:System.Object.Finalize%2A?displayProperty=nameWithType> , definiując [destruktora](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implementowanie wzorca usuwania dla klasy pochodnej

Klasą pochodną klasy, która implementuje <xref:System.IDisposable> nie powinny implementować interfejs <xref:System.IDisposable>, ponieważ Implementacja klasy podstawowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> jest dziedziczona przez jej klas pochodnych. Tak więc, aby zaimplementować wzorzec usuwania dla klasy pochodnej, należy dostarczyć następujące elementy:  
  
* A `protected``Dispose(Boolean)` metodę, która zastępuje metodę klasy podstawowej i wykonuje faktyczną pracę zwolnienie zasobów klasy pochodnej. Tej metody należy także wywołać `Dispose(Boolean)` metody podstawowej klasy i przekaż go wartość `true` dla *disposing* argumentu.  
  
* Każda klasa pochodzi od <xref:System.Runtime.InteropServices.SafeHandle> który opakowuje niezarządzanego zasobu (zalecane) lub zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody. <xref:System.Runtime.InteropServices.SafeHandle> Klasa udostępnia finalizatorze zwalnia z konieczności kodu. Jeśli podasz finalizator powinny wywoływać `Dispose(Boolean)` przeciążenia z *disposing* argument `false`.  
  
Poniżej przedstawiono ogólny schemat implementowania wzorca usuwania dla klasy pochodnej, w którym jest używane bezpieczne dojście:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> W poprzednim przykładzie użyto <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu w celu zilustrowania wzorzec; dowolny obiekt pochodną <xref:System.Runtime.InteropServices.SafeHandle> może być użyty. Należy pamiętać, że przykładzie nie prawidłowo utworzyć wystąpienia jego <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiektu.  
  
Poniżej przedstawiono ogólne wzorca w zakresie implementacji wzorca dispose dla klasy pochodnej, która zastępuje <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> W języku C#, Zastąp <xref:System.Object.Finalize%2A?displayProperty=nameWithType> , definiując [destruktora](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Używanie bezpiecznych dojść

Pisanie kodu dla finalizatora obiektu to złożone zadanie, które może powodować problemy, jeśli nie zostanie wykonane prawidłowo. Dlatego zaleca się, że utworzymy <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> obiektów zamiast wykonania finalizator.  
  
Klasy wyprowadzone z <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy uprościć kwestie okresu istnienia obiektu przypisując i zwalniania uchwytów bez przeszkód. Zawierają finalizator krytyczny, który gwarantuje działanie w trakcie zwalniania domeny aplikacji. Aby uzyskać więcej informacji o zaletach korzystania bezpieczne dojście, zobacz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Następujące klasy w pochodne <xref:Microsoft.Win32.SafeHandles> bezpiecznego dojścia Podaj przestrzeń nazw:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, I <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> klasy dla plików, plików mapowanych na pamięć i potoków.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Klasy widoków pamięci.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, I <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> klasy dla konstrukcji kryptografii.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Klasy dla kluczy rejestru.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Klasy dla uchwyty oczekiwania.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy bazowej

Poniższy przykład przedstawia wzorzec dispose dla klasy podstawowej, `DisposableStreamResource`, że używa bezpieczne dojście do hermetyzować zasoby niezarządzane. Definiuje `DisposableResource` klasy, która używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> opakowywać <xref:System.IO.Stream> obiekt, który reprezentuje plik. `DisposableResource` Metoda również zawiera tylko jedną właściwość `Size`, która zwraca wartość całkowita liczba bajtów w strumieniu plików.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Używanie bezpiecznego dojścia w celu implementacji wzorca usuwania dla klasy pochodnej

Poniższy przykład przedstawia wzorzec dispose dla klasy pochodnej, `DisposableStreamResource2`, która dziedziczy `DisposableStreamResource` klasy przedstawionych w poprzednim przykładzie. Klasa dodaje dodatkowe metody `WriteFileInfo`i używa <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> obiekt do zakodowania dojście plik zapisywalny.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

<xref:System.GC.SuppressFinalize%2A>   
<xref:System.IDisposable>   
<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>   
<xref:Microsoft.Win32.SafeHandles>   
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>   
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>   
[Porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)   
[Wzorzec Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md)
