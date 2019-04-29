---
title: Format pliku zestawu .NET
description: Dowiedz się więcej o formacie pliku zestawu .NET, który jest używany do opisywania i zawierać aplikacji .NET i bibliotek.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 0bde31a004b1952be488569f89cfd3b129c82771
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627954"
---
# <a name="net-assembly-file-format"></a>Format pliku zestawu .NET

.NET definiuje format pliku binarnego — "assembly" — służy do w pełni opisują, a także zawierać programy platformy .NET. Zestawy są używane programy, a także wszelkie zależne biblioteki. .NET program mogą być wykonywane jako jeden lub więcej zestawów z nie innych wymaganych artefaktów, poza odpowiedniej implementacji .NET. Natywne zależności, w tym systemie operacyjnym interfejsów API, są oddzielne zastrzeżenia i nie znajdują się w ciągu formatu zestawu .NET, chociaż są czasami określane w formacie (na przykład WinRT).

> Każdy składnik interfejsu wiersza polecenia niesie ze sobą metadanych dla deklaracji, implementacji i określonego odwołania do tego składnika. Dlatego metadane specyficzne dla danego składnika jest określany jako metadane składnika i Wynikowy składnik jest nazywany można samoopisujące — ECMA 335 I.9.1, składniki i zestawy.

Format jest w pełni określony i standaryzowane jako [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Wszystkie środowiska uruchomieniowe i Kompilatory języka .NET, użyj tego formatu. Obecność udokumentowane i rzadko aktualizowane format binarny został głównych korzyści (prawdopodobnie wymaganie) współdziałania. Format ostatniej aktualizacji w sposób merytorycznych w 2005 r. (.NET 2.0), aby pomieścić typy ogólne i architektury procesora.

Format jest niezainteresowana Procesora i systemu operacyjnego. Został on użyty w ramach implementacji platformy .NET, przeznaczonych na wiele procesorów i mikroukłady. Sam format ma dziedzictwa Windows, ale jest implementable w dowolnym systemie operacyjnym. Prawdopodobnie największy wybór współdziałania w ramach systemu operacyjnego jest, że większość wartości są przechowywane w formacie little-endian. Nie ma określonych koligacji do rozmiaru wskaźnika maszyny (na przykład 32-bitowy, 64-bitowy).

Format zestawu .NET jest również bardzo opisowe informacje o strukturze dany program lub biblioteki. Opisano w nim wewnętrznych składników zestawu, w szczególności: odwołania do zestawów i typów zdefiniowanych oraz ich struktury wewnętrznej. Narzędzia i interfejsy API może odczytywać i przetwarzać te informacje do wyświetlania lub podjąć decyzje dotyczące programowego.

## <a name="format"></a>Format

Format binarny platformy .NET jest oparty na Windows [pliku PE](https://en.wikipedia.org/wiki/Portable_Executable) formatu. W rzeczywistości biblioteki klas platformy .NET są zgodność Windows PEs i pojawiają się na pierwszy rzut oka Windows biblioteki dołączane dynamicznie (dll) lub aplikacji plików wykonywalnych (exe). Jest to bardzo przydatne cecha w Windows, w którym można udają natywnych plików binarnych z pliku wykonywalnego i otrzymujesz niektóre z tych samych traktowania (na przykład ładowania systemu operacyjnego, narzędzia PE).

![Zestaw nagłówków](../media/assembly-format/assembly-headers.png)

Zestaw nagłówków z ECMA 335 II.25.1, struktura formatu plików środowiska uruchomieniowego.

## <a name="processing-the-assemblies"></a>Przetwarzanie zestawów

Istnieje możliwość zapisu do procesu zestawów narzędzi lub interfejsów API. Informacje o zestawie umożliwia podejmowanie decyzji programowe w czasie wykonywania, ponownego tworzenia zestawów, zapewniając interfejsu API funkcji IntelliSense w edytorze i generowanie dokumentacji. <xref:System.Reflection?displayProperty=nameWithType> i [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) są dobrym przykładem narzędzia, które są często używane w tym celu.
