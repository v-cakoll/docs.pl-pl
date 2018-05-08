---
title: Format pliku zestawu .NET
description: Dowiedz się więcej o formacie pliku zestawu .NET, który jest używany do opisywania i zawierają aplikacji .NET i bibliotek.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 219e2872ab58980ef7b4bce8e901341d8893a1a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-assembly-file-format"></a>Format pliku zestawu .NET

.NET definiuje format pliku binarnego — "zestawu" — służy do pełni opisywania i zawierają programy .NET. Zestawy są używane do samych programów, a także wszelkich zależnych bibliotek. .NET program mogą być wykonywane jako jeden lub więcej zestawów z nie innych wymaganych artefaktów, po wykonaniu odpowiednich .NET. Natywnego zależności, w tym system operacyjny interfejsów API, są oddzielne problemu i nie są zawarte w formacie zestawu .NET, mimo że czasami są opisane w tym formacie (na przykład WinRT).

> Każdy składnik interfejsu wiersza polecenia niesie metadanych dla deklaracji, implementacji i odwołuje się do określonego dla tego składnika. W związku z tym metadane specyficzne dla składnika jest określana jako składnik metadane, a wynikowy składnik jest nazywany można samoopisujące — z ECMA 335 I.9.1, składników i zestawów.

W pełni określić i znormalizowany w formacie [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Użyj tego formatu, wszystkie kompilatory .NET i środowisk uruchomieniowych. Obecność udokumentowanych i rzadko zaktualizowane format binarny został najważniejszych korzyści (raczej wymaganie) współdziałanie. Format ostatniej aktualizacji w sposób merytorycznych w 2005 (.NET 2.0), aby pomieścić ogólne i architektury procesora.

Format jest funkcja Procesora i systemu operacyjnego. Został on użyty jako część implementacji .NET, które odnoszą się do wielu procesorów i mikroukłady. Gdy sam format ma dziedzictwa systemu Windows, jest implementable w dowolnym systemie operacyjnym. Jego raczej najważniejszych wybór współdziałania systemu operacyjnego jest, że większość wartości są przechowywane w formacie little endian. Nie ma określonego koligacji do rozmiaru wskaźnika maszyny (na przykład 32-bitowy, 64-bitowe).

Format zestawu .NET jest również bardzo opisowe informacje o strukturze danego programu lub biblioteki. Opisuje wewnętrznych składników zestawu, w szczególności: odwołania do zestawów i zdefiniowanych typów i ich wewnętrznej struktury. Narzędzia i interfejsy API może odczytywać i przetwarzać te informacje do wyświetlania lub podjąć decyzje dotyczące programistyczny.

## <a name="format"></a>Format

Format binarny .NET zależy od systemu Windows [plik PE](https://en.wikipedia.org/wiki/Portable_Executable) format. W rzeczywistości bibliotek klas .NET są zgodność PEs systemu Windows i są wyświetlane na pierwszy rzut systemu Windows biblioteki dołączanej dynamicznie (dll) lub aplikacji pliki wykonywalne (exe). Jest to bardzo przydatne cecha w systemie Windows, w którym można udają natywne pliki binarne pliku wykonywalnego i wykonać niektóre taki sam sposób (na przykład ładowania systemu operacyjnego, narzędzia PE).

![Nagłówki zestawu](./media/assembly-format/assembly-headers.png)

Nagłówki zestawu z ECMA 335 II.25.1, strukturę środowiska uruchomieniowego formatu pliku.

## <a name="processing-the-assemblies"></a>Przetwarzanie zestawów

Istnieje możliwość zapisu do procesu zestawów narzędzia lub interfejsów API. Informacje o zestawie umożliwia podejmowanie decyzji programowych w czasie wykonywania, ponowne zapisywanie zestawów, zapewniając interfejsu API IntelliSense w edytorze i generowanie dokumentacji. <xref:System.Reflection?displayProperty=nameWithType> i [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) są dobrym przykładem narzędzia, które są często używane w tym celu.
