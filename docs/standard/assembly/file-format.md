---
title: Format pliku zestawu .NET
description: Dowiedz się więcej o formacie pliku zestawu platformy .NET, który jest używany do opisywania i zawierania aplikacji i bibliotek platformy .NET.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 5ef5d459195bea752ec5380f2853d8011cb189aa
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666633"
---
# <a name="net-assembly-file-format"></a>Format pliku zestawu .NET

Platforma .NET definiuje format pliku binarnego — "zestaw" — używany do pełnego opisywania i zawiera programy .NET. Zestawy są używane na potrzeby programów, a także do wszystkich bibliotek zależnych. Program .NET można wykonać jako jeden lub więcej zestawów bez żadnych innych wymaganych artefaktów, poza odpowiednią implementacją platformy .NET. Natywne zależności, w tym interfejsy API systemu operacyjnego, są oddzielnymi problemami i nie są zawarte w formacie zestawu .NET, chociaż są czasami opisane w tym formacie (na przykład WinRT).

> Każdy składnik interfejsu wiersza polecenia przenosi metadane dla deklaracji, implementacji i odwołań specyficznych dla tego składnika. W związku z tym metadane specyficzne dla składnika są określane jako metadane składników, a składnik uzyskany jest uważany za własny opis — od ECMA 335 I. 9.1 składników i zestawów.

Format jest w pełni określony i znormalizowany jako [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Wszystkie kompilatory i środowiska uruchomieniowe platformy .NET używają tego formatu. Obecność udokumentowanego i rzadko aktualizowanego formatu binarnego jest ważnym korzyścią (raczej wymaganie) dla współdziałania. Format został ostatnio zaktualizowany w sposób istotny w 2005 (.NET 2,0) w celu uwzględnienia ogólnych i architektury procesora.

Format to procesor CPU i OS-niezależny od. Jest ona używana jako część implementacji platformy .NET, które są przeznaczone dla wielu układów i procesorów. Chociaż sam format ma dziedzictwo systemu Windows, można go zaimplementować w dowolnym systemie operacyjnym. Raczej najbardziej znaczący wybór dla interoperacyjności systemu operacyjnego polega na tym, że większość wartości jest przechowywanych w formacie little-endian. Nie ma konkretnej koligacji z rozmiarem wskaźnika maszyny (na przykład 32-bitowym, 64-bitowym).

Format zestawu .NET jest również bardzo opisową strukturą danego programu lub biblioteki. Opisuje wewnętrzne składniki zestawu, w tym: odwołania do zestawów i typy zdefiniowane oraz ich struktura wewnętrzna. Narzędzia lub interfejsy API mogą odczytywać i przetwarzać te informacje w celu wyświetlania lub podejmowania decyzji programistycznych.

## <a name="format"></a>Format

Format binarny platformy .NET jest oparty na formacie [pliku Windows PE](https://en.wikipedia.org/wiki/Portable_Executable) . W rzeczywistości biblioteki klas platformy .NET są zgodne z modułami MFC systemu Windows i pojawiają się na pierwszy rzut oka jako biblioteki dołączane dynamicznie (dll) systemu Windows lub pliki wykonywalne aplikacji (exe). Jest to bardzo przydatna cecha w systemie Windows, w której mogą one być maskowane jako natywne pliki binarne plików wykonywalnych i uzyskać niektóre z tych samych traktowania (na przykład ładowania systemu operacyjnego, narzędzi PE).

![Nagłówki zestawów](../media/assembly-format/assembly-headers.png)

Nagłówki zestawów z ECMA 335 II. 25.1, struktura formatu pliku środowiska uruchomieniowego.

## <a name="processing-the-assemblies"></a>Przetwarzanie zestawów

Istnieje możliwość pisania narzędzi lub interfejsów API do przetwarzania zestawów. Informacje o zestawie umożliwiają podejmowanie decyzji programistycznych w czasie wykonywania, ponowne pisanie zestawów, dostarczanie interfejsu API IntelliSense w edytorze i generowanie dokumentacji. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType>, i [mono. Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) są dobrymi przykładami narzędzi, które są często używane do tego celu.
