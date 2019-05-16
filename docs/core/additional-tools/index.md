---
title: Dodatkowe narzędzia interfejsu wiersza polecenia platformy .NET core
description: Omówienie dodatkowe narzędzia można zainstalować obsługi i rozszerzania funkcji platformy .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 75c74c16367bacf66fa2fb56d7666a07f7274aff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631959"
---
# <a name="net-core-additional-tools-overview"></a>Omówienie narzędzia dodatkowe platformy .NET core

W tej sekcji kompiluje listę narzędzi, które obsługują i rozszerzania funkcji platformy .NET Core, oprócz [platformy .NET Core interfejsu wiersza polecenia (CLI)](../tools/index.md) narzędzia.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzia WCF Web Service Reference](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF (Windows Communication Foundation) jest dostawcę usług połączonych programu Visual Studio, zgłaszający jego przedstawiają po raz w [programu Visual Studio 2017 w wersji 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). To narzędzie służy do pobierania metadanych z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje plik źródłowy jest zgodny z platformą .NET Core, definicji klasy serwera proxy usług WCF za pomocą metod, które umożliwiają dostęp do operacji usługi sieci web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Narzędzia dotnet svcutil WCF](dotnet-svcutil-guide.md)

Narzędzia dotnet svcutil WCF (Windows Communication Foundation) jest narzędziem wiersza polecenia platformy .NET Core, które służy do pobierania metadanych z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje plik źródłowy zgodnych z platformą .NET Core, definicji klasy serwera proxy usług WCF za pomocą metod Czy można użyć do dostępu do operacji usługi sieci web.
**Narzędzia svcutil dotnet** narzędzie jest alternatywnych opcji [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) dostawcy usług, który po raz pierwszy wysłane połączona programu Visual Studio z programem Visual Studio v15.5 2017 r. **Narzędzia svcutil dotnet** narzędzia jako narzędzie wiersza polecenia platformy .NET Core, są dostępne dla wielu platform w systemie Linux, macOS i Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md)

Od programu .NET Framework można wstępnie wygenerować zestawu serializacji przy użyciu narzędzia svcutil. Pakiet NuGet dotnet svcutil.xmlserializer zapewnia podobne funkcje na platformie .NET Core. Wstępnie generuje C# kodu serializacji dla typów w aplikacji klienckiej, które są używane przez kontraktu usługi WCF i może być serializowany przez <xref:System.Xml.Serialization.XmlSerializer>. Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów z tych typów.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) to rozwiązanie dla biblioteki .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów, które są zawarte w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiekty, które z tych typów, przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.
