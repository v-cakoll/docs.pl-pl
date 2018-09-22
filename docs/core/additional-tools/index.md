---
title: Dodatkowe narzędzia .NET core
description: Przegląd dodatkowe narzędzia, które obsługują i rozszerzania funkcji platformy .NET Core.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: c64dddbe36b789a695c2603e78b29b38d8718f95
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586886"
---
# <a name="net-core-additional-tools"></a>Dodatkowe narzędzia .NET core

W tej sekcji kompiluje listę narzędzi, które obsługują i rozszerzania funkcji platformy .NET Core, oprócz [platformy .NET Core interfejsu wiersza polecenia (CLI)](../tools/index.md) narzędzia.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzia WCF Web Service Reference](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF (Windows Communication Foundation) jest dostawcę usług połączonych programu Visual Studio, zgłaszający jego przedstawiają po raz w [programu Visual Studio 2017 w wersji 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools). To narzędzie służy do pobierania metadanych z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje plik źródłowy jest zgodny z platformą .NET Core, definicji klasy serwera proxy usług WCF za pomocą metod, które umożliwiają dostęp do operacji usługi sieci web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Narzędzia dotnet svcutil WCF](dotnet-svcutil-guide.md)

Narzędzia dotnet svcutil WCF (Windows Communication Foundation) jest narzędziem wiersza polecenia platformy .NET Core, które służy do pobierania metadanych z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje plik źródłowy zgodnych z platformą .NET Core, definicji klasy serwera proxy usług WCF za pomocą metod Czy można użyć do dostępu do operacji usługi sieci web. **Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, który po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r. **Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) to rozwiązanie dla biblioteki .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów, które są zawarte w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiekty, które z tych typów, przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.