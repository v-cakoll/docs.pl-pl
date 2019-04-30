---
title: Ułatwianie debugowania na platformie .NET obrazu
description: Dowiedz się, jak skonfigurować wykonywalny obraz dla zmienia ułatwiają debugowanie przy użyciu środowiska IDE i opcje wiersza polecenia.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bab707afb059d4fcbd46a9ee54edead991be523
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754222"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Ułatwianie debugowania na platformie .NET obrazu

Podczas kompilowania niezarządzanego kodu można za pomocą odpowiednich przełączników środowiska IDE lub opcji wiersza polecenia skonfigurować wykonywalny obraz na potrzeby debugowania. Na przykład, można użyć /**Zi** opcji wiersza polecenia w programie Visual C++ można zażądać wyemitowania plików symboli debugowania (plików z rozszerzeniem .pdb). Podobnie /**Od** opcji wiersza polecenia informuje kompilator, aby wyłączyć optymalizację. Powstały kod działa wolniej, ale jest łatwiejszy do debugowania, w razie potrzeby.

Podczas kompilowania .NET Framework kodu zarządzanego, kompilatory, takie jak Visual C++, Visual Basic i C# kompilują program źródłowy do języka Microsoft intermediate language (MSIL). MSIL jest kompilowany dokładnie na czas, tuż przed wykonaniem do macierzystego kodu maszynowego. Podobnie jak w przypadku kodu niezarządzanego za pomocą odpowiednich przełączników środowiska IDE lub opcji wiersza polecenia można na potrzeby debugowania skonfigurować wykonywalny obraz. Można również skonfigurować kompilację JIT dla debugowania w taki sam sposób.

Taka konfiguracja JIT ma dwa aspekty:

- Możesz poprosić kompilator JIT, aby wygenerować informacje ze śledzenia. Po włączeniu tej opcji debuger może porównywać łańcuch kodu języka MSIL z jego odpowiednikiem w kodzie maszynowym oraz śledzić, gdzie są przechowywane lokalne zmienne i argumenty funkcji. Począwszy od programu .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia, więc nie trzeba wysłać żądanie.

- Możesz poprosić kompilator JIT braku optymalizacji powstającego kodu maszynowego.

Normalnie, kompilator generujący kod w języku MSIL ustawia te opcje kompilatora JIT, na podstawie przełączników środowiska IDE lub opcji wiersza polecenia, które określisz, na przykład /**Od**.

Czasami trzeba zmienić zachowanie kompilatora JIT, tak aby generowany przez niego kod maszynowy był łatwiejszy do debugowania. Na przykład warto wygenerować informacje ze śledzenia kompilatora JIT dla kompilacji detalicznej lub optymalizacji kontrolek. Należy do tego celu użyć pliku inicjującego (.ini).

Na przykład, jeśli zestaw, który chcesz debugować jest nazywana *MyApp.exe*, możesz utworzyć plik tekstowy o nazwie *MyApp.ini*, w tym samym folderze co *MyApp.exe*, który zawiera te trzy wiersze:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Dla każdej opcji można ustawić wartość 0 lub 1. Każda niezdefiniowana opcja domyślnie przyjmuje wartość 0. Ustawienie w opcji `GenerateTrackingInfo` wartości 1 i w opcji `AllowOptimize` wartości 0 zapewni najłatwiejsze debugowanie.

Począwszy od programu .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia niezależnie od wartości `GenerateTrackingInfo`; jednak `AllowOptimize` wartość wciąż daje efekt. Korzystając z [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) wstępnej kompilacji obrazu natywnego, bez optymalizacji, musi znajdować się w folderze docelowym przy użyciu pliku ini `AllowOptimize=0` kiedy wykonuje Ngen.exe. Jeśli istnieje wstępnie skompilowany zestaw bez optymalizacji, należy usunąć wstępnie skompilowany kod za pomocą NGen.exe **/ uninstall** możliwość przed ponownym uruchomieniu Ngen.exe wstępnie skompilować kod jako zoptymalizowany. Jeśli plik .ini nie jest obecny w folderze, domyślnie Ngen.exe wstępnie kompiluje kod z optymalizacją.

Klasa <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> kontroluje ustawienia zestawu. **DebuggableAttribute** zawiera dwa pola tę kontrolkę, czy kompilator JIT należy zoptymalizować i/lub generować informacje ze śledzenia. Począwszy od programu .NET Framework w wersji 2.0 kompilator JIT zawsze generuje informacje ze śledzenia.

Dla kompilacji detalicznej kompilatory nie ustawiają żadnej **DebuggableAttribute**. Domyślnie kompilator JIT generuje o najwyższej wydajności i najtrudniejszego do debugowania kodu maszynowego. Włączenie funkcji śledzenia w kompilatorze JIT obniża wydajność nieznacznie, natomiast wyłączenie optymalizacji zmniejsza ją wyraźnie.

**DebuggableAttribute** ma zastosowanie do całego zestawu w czasie, a nie do poszczególnych modułów w zestawie. Narzędzia programistyczne w związku z tym muszą dołączać niestandardowe atrybuty do tokenu metadanych zestawu, jeśli zestawu została już utworzona, lub do klasy o nazwie **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. Te promuje następnie narzędzie ALink **DebuggableAttribute** atrybuty z każdego modułu do zestawu staną się częścią. W przypadku konfliktu operacja ALink kończy się niepowodzeniem.

> [!NOTE]
> W programie .NET Framework w wersji 1.0 kompilator Microsoft Visual C++ dodaje **DebuggableAttribute** podczas **/CLR** i **/zi** określono opcje kompilatora. W wersji 1.1 programu .NET Framework, należy dodać **DebuggableAttribute** ręcznie w kodzie albo użyć **/assemblydebug** — opcja konsolidatora.

## <a name="see-also"></a>Zobacz także

- [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)
- [Włączanie debugowania dołączania JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [Włączanie profilowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
