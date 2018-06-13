---
title: Ułatwianie debugowania obrazu
ms.date: 03/30/2017
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c58008bc621ea95fbb2e4cc5e7d4521576aca37c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391049"
---
# <a name="making-an-image-easier-to-debug"></a>Ułatwianie debugowania obrazu
Podczas kompilowania niezarządzanego kodu można za pomocą odpowiednich przełączników środowiska IDE lub opcji wiersza polecenia skonfigurować wykonywalny obraz na potrzeby debugowania. Na przykład można użyć /**Zi** opcji wiersza polecenia w programie Visual C++ można zażądać Emituj debugowania plików symboli (.pdb rozszerzenia pliku). Podobnie /**Od** opcji wiersza polecenia informuje kompilator, aby wyłączyć optymalizacji. Powstały kod działa wolniej, ale w razie potrzeby łatwiej go debugować.  
  
 Podczas kompilowania zarządzanego kodu środowiska .NET Framework kompilatory takie jak Visual C++, Visual Basic i C# kompilują program źródłowy do języka Microsoft Intermediate Language (MSIL). Kod w języku MSIL tuż przed wykonaniem jest kompilowany dokładnie na czas do macierzystego kodu maszynowego. Podobnie jak w przypadku kodu niezarządzanego za pomocą odpowiednich przełączników środowiska IDE lub opcji wiersza polecenia można na potrzeby debugowania skonfigurować wykonywalny obraz. W bardzo podobny sposób można również skonfigurować kompilowanie dokładnie na czas (JIT) w celu debugowania.  
  
 Taka konfiguracja JIT ma dwa aspekty:  
  
-   W kompilatorze JIT można włączyć generowanie informacji ze śledzenia. Po włączeniu tej opcji debuger może porównywać łańcuch kodu języka MSIL z jego odpowiednikiem w kodzie maszynowym oraz śledzić, gdzie są przechowywane lokalne zmienne i argumenty funkcji.  W programie .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia, dlatego nie trzeba specjalnie włączać takiej opcji.  
  
-   W kompilatorze JIT można włączyć opcję braku optymalizacji powstającego kodu maszynowego.  
  
 Zwykle, kompilator generuje MSIL ustawia tych opcji kompilatora JIT, na podstawie przełączników IDE lub opcji wiersza polecenia można określić, na przykład /**Od**.  
  
 Czasami trzeba zmienić zachowanie kompilatora JIT, tak aby generowany przez niego kod maszynowy był łatwiejszy do debugowania. Na przykład warto wygenerować informacje ze śledzenia kompilatora JIT dla kompilacji detalicznej lub optymalizacji kontrolek. Należy do tego celu użyć pliku inicjującego (.ini).  
  
 Jeśli na przykład zestaw, który ma być debugowany, nazywa się MyApp.exe, w folderze z plikiem MyApp.exe można utworzyć plik tekstowy o nazwie MyApp.ini zawierający poniższe trzy wiersze:  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Dla każdej opcji można ustawić wartość 0 lub 1. Każda niezdefiniowana opcja domyślnie przyjmuje wartość 0. Ustawienie w opcji `GenerateTrackingInfo` wartości 1 i w opcji `AllowOptimize` wartości 0 zapewni najłatwiejsze debugowanie.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia, niezależnie od wartości atrybutu `GenerateTrackingInfo`. Tym niemniej wartość `AllowOptimize` wciąż daje efekt. Korzystając z [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) wstępnej kompilacji obrazu macierzystego bez optymalizacji, plik .ini musi znajdować się w folderze docelowym z `AllowOptimize=0` po wykonuje Ngen.exe. Jeśli zostały wstępnie skompilowana zestawu bez optymalizacji, należy usunąć kod wstępnie skompilowana przy użyciu NGen.exe **/ uninstall** opcji przed uruchomienie Ngen.exe wstępnej kompilacji kodu, ponieważ zoptymalizowane. Jeśli w folderze nie ma pliku .ini, domyślnie program Ngen.exe wstępnie kompiluje kod z optymalizacją.  
  
> [!NOTE]
>  Klasa <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> kontroluje ustawienia zestawu. **DebuggableAttribute** zawiera dwa pola, które rekordu ustawienia dla tego, czy przy użyciu kompilatora JIT powinien optymalizacji i/lub Generuj informacje o śledzeniu. W programie .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia.  
  
> [!NOTE]
>  Dla kompilację detalicznych kompilatory nie należy ustawiać żadnego **DebuggableAttribute**. Domyślne zachowanie kompilatora JIT prowadzi do wygenerowaniu kodu maszynowego o najwyższej wydajności i najtrudniejszego do debugowania. Włączenie funkcji śledzenia w kompilatorze JIT obniża wydajność nieznacznie, natomiast wyłączenie optymalizacji zmniejsza ją wyraźnie.  
  
> [!NOTE]
>  **DebuggableAttribute** ma zastosowanie do całego zestawu w czasie, a nie do poszczególnych modułów w zestawie. Narzędzia deweloperskie w związku z tym należy dołączyć atrybutów niestandardowych do tokenu metadanych zestawu, jeśli zestawu została już utworzona, lub do klasy o nazwie **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. Narzędzia ALink następnie propaguje je **DebuggableAttribute** atrybutów z poszczególnych modułów do zestawu stają się one częścią. W razie istnienia konfliktu operacja ALink kończy się niepowodzeniem.  
  
> [!NOTE]
>  W wersji 1.0 programu .NET Framework, dodaje kompilator Microsoft Visual C++ **DebuggableAttribute** podczas **/CLR** i **/zi** — opcje kompilatora zostały określone. W wersji 1.1 platformy .NET, należy dodać **DebugabbleAttribute** ręcznie w kodu lub użycie **/ASSEMBLYDEBUG** — opcja konsolidatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)  
 [Włączanie debugowania dołączania JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [Włączenie profilowania](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
