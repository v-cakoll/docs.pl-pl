---
title: Format pliku zestawu .NET
description: Dowiedz się więcej o formacie zestawu .NET, który jest używany do opisywania i zawierają aplikacje i biblioteki .NET.
author: richlander
ms.date: 08/20/2019
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 4cf6522d66d7a1efccde45078768a773db6e6cb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711587"
---
# <a name="net-assembly-file-format"></a>Format pliku zestawu .NET

Program .NET definiuje binarny format pliku, *zestaw,* który jest używany do pełnego opisywania i zawierania programów .NET. Zestawy są używane dla samych programów, a także dla wszystkich bibliotek zależnych. Program .NET może być wykonywany jako jeden lub więcej zestawów, bez innych wymaganych artefaktów, poza odpowiednią implementacją .NET. Zależności macierzyste, w tym interfejsy API systemu operacyjnego, są oddzielnym problemem i nie są zawarte w formacie zestawu .NET, chociaż czasami są opisane w tym formacie (na przykład WinRT).

> Każdy składnik cli zawiera metadane dla deklaracji, implementacji i odwołań specyficznych dla tego składnika. W związku z tym metadane specyficzne dla składnika jest określany jako metadanych składnika, a składnik wynikowy mówi się, że samoopisujące - z ECMA 335 I.9.1, Składniki i zespoły.

Format jest w pełni określony i znormalizowany jako [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Wszystkie kompilatory i uruchamianie .NET używają tego formatu. Obecność udokumentowanego i rzadko aktualizowanego formatu binarnego była główną korzyścią (prawdopodobnie wymogiem) dla interoperacyjności. Format został ostatnio zaktualizowany w sposób merytoryczny w 2005 r. (.NET 2.0) w celu uwzględnienia typów ogólnych i architektury procesora.

Format jest cpu- i os-agnostyk. Został on użyty jako część implementacji .NET, które są przeznaczone dla wielu układów scalonych i procesorów. Chociaż sam format ma dziedzictwo systemu Windows, można go wdrożyć w dowolnym systemie operacyjnym. Jego prawdopodobnie najbardziej znaczącym wyborem dla interoperacyjności os jest to, że większość wartości są przechowywane w formacie little-endian. Nie ma określonego koligacji do rozmiaru wskaźnika maszyny (na przykład 32-bitowy, 64-bitowy).

Format zestawu .NET jest również bardzo opisowy w strukturze danego programu lub biblioteki. Opisuje wewnętrzne komponenty złożenia, w szczególności odniesienia do złożenia i zdefiniowane typy oraz ich wewnętrzną strukturę. Narzędzia lub interfejsy API mogą odczytywać i przetwarzać te informacje w celu wyświetlenia lub podejmowania decyzji programowych.

## <a name="format"></a>Format

Format binarny .NET jest oparty na formacie pliku Środowiska Windows [PE.](https://en.wikipedia.org/wiki/Portable_Executable) W rzeczywistości biblioteki klas .NET są zgodne z adresami P systemu Windows i są wyświetlane na pierwszy rzut oka jako biblioteki łączy dynamicznych systemu Windows (DLL) lub pliki wykonywalne aplikacji (EXE). Jest to bardzo przydatna cecha w systemie Windows, gdzie mogą podszywać się pod natywne pliki końcowe i uzyskać takie samo traktowanie (na przykład obciążenie systemu operacyjnego, narzędzia PE).

![Nagłówki zestawów](../media/assembly-format/assembly-headers.png)

Nagłówki zestawów z ECMA 335 II.25.1, Struktura formatu pliku czasu wykonywania.

## <a name="process-the-assemblies"></a>Przetwarzanie złożeń

Istnieje możliwość pisania narzędzi lub interfejsów API do przetwarzania zestawów. Informacje o złożeniu umożliwiają podejmowanie decyzji programowych w czasie wykonywania, ponowne pisanie zestawów, dostarczanie api IntelliSense w edytorze i generowanie dokumentacji. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType>i [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) są dobrymi przykładami narzędzi, które są często używane do tego celu.
