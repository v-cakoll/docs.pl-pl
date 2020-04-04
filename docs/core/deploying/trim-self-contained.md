---
title: Przycinanie samodzielnych aplikacji
description: Dowiedz się, jak przycinać samodzielne aplikacje, aby zmniejszyć ich rozmiar. .NET Core pakiety środowiska wykonawczego z aplikacją, która jest publikowana samodzielnie i zazwyczaj zawiera więcej środowiska wykonawczego, a następnie jest konieczne.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665636"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Przycinanie samodzielnych wdrożeń i plików wykonywalnych

Podczas publikowania aplikacji samodzielny, .NET Core środowiska uruchomieniowego jest powiązany z aplikacją. Ten pakiet dodaje znaczną ilość zawartości do spakowanej aplikacji.

Jeśli chodzi o wdrażanie aplikacji, rozmiar jest często ważnym czynnikiem. Utrzymanie rozmiaru aplikacji pakietu tak małe, jak to możliwe jest zazwyczaj celem dla deweloperów aplikacji.

W zależności od złożoności aplikacji do uruchomienia aplikacji wymagany jest tylko podzbiór środowiska wykonawczego. Te nieużywane części środowiska wykonawczego są niepotrzebne i mogą być przycinane z spakowanej aplikacji.

> [!NOTE]
> Przycinanie jest funkcją eksperymentalną w .NET Core 3.1 i jest dostępne _tylko_ dla aplikacji, które są publikowane samodzielnie.

## <a name="trim-your-application"></a>Przycinanie aplikacji

W poniższym przykładzie pokazano, jak przyciąć aplikację za pomocą polecenia [publikowania dotnetu:](../tools/dotnet-publish.md)

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

Funkcja przycinania działa przez sprawdzenie plików binarnych aplikacji w celu odnajdywania i tworzenia wykresu wymaganych zestawów środowiska wykonawczego. Pozostałe zestawy środowiska wykonawczego, do których nie ma odniesienia, są przycinane.

## <a name="trimming-issues-when-using-reflection"></a>Problemy z przycinaniem podczas korzystania z odbicia

Istnieją scenariusze, w których funkcja przycinania nie będzie wykryć odwołań. Na przykład aplikacja, która używa odbicia może uruchomić w tym problemie, ponieważ zależność od zestawu będzie znana tylko w czasie wykonywania.

Przycinanie jest tylko problem, jeśli użycie odbicia zależy od zestawu środowiska wykonawczego, który nie odwołuje się bezpośrednio. Należy pamiętać, że kod aplikacji może nie używać odbicia bezpośrednio, ale zestaw innych firm, do którego się odwołujesz, może go używać.

Gdy kod odwołuje się do interfejsu API za pomocą odbicia i nie chcesz, aby konsolidator przycinał zestaw zawierający ten interfejs API, można zmodyfikować plik projektu, aby wykluczyć zestaw z procesu przycinania. W poniższym przykładzie pokazano, `System.Security` jak zapobiec przycinaniu zestawu wywoływanego:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Wdrożenie aplikacji .NET Core](index.md)
