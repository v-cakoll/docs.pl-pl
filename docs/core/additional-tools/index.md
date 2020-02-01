---
title: Dodatkowe narzędzia
description: Omówienie dodatkowych narzędzi, które można zainstalować, które obsługują i poszerzają funkcje platformy .NET Core.
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 23b94ceef729cdc3d83032e3897312eb1d1afd79
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920934"
---
# <a name="net-core-additional-tools-overview"></a>Dodatkowe narzędzia platformy .NET Core — Omówienie

W tej sekcji została skompilowana lista narzędzi, które obsługują i poszerzają funkcje programu .NET Core, a także interfejs wiersza polecenia platformy .NET Core.

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[Narzędzie do dezinstalacji programu .NET Core](uninstall-tool.md)

[Narzędzie do dezinstalacji programu .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umożliwia wyczyszczenie zestawów .NET Core i środowiska uruchomieniowego w systemie, tak aby były nadal tylko określone wersje. Dostępna jest kolekcja opcji, aby określić, które wersje zostały odinstalowane.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzie referencyjne usługi sieci Web WCF](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF (Windows Communication Foundation) to Dostawca usługi połączonej z programu Visual Studio, który wykonał udostępnione w programie [Visual studio 2017 w wersji 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). To narzędzie pobiera metadane z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub w pliku WSDL. Generuje plik źródłowy zgodny z platformą .NET Core, definiując klasę serwera proxy WCF przy użyciu metod, których można użyć w celu uzyskania dostępu do operacji usługi sieci Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet — narzędzie Svcutil](dotnet-svcutil-guide.md)

Narzędzie WCF (Windows Communication Foundation) dotnet-Svcutil jest narzędziem platformy .NET, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL. Generuje plik źródłowy zgodny z platformą .NET Core, definiując klasę serwera proxy WCF przy użyciu metod, których można użyć w celu uzyskania dostępu do operacji usługi sieci Web.

Narzędzie **dotnet-Svcutil** jest alternatywną opcją dla [**referencyjnej usługi sieci Web programu WCF**](wcf-web-service-reference-guide.md) , która jest dostarczana z programem Visual studio 2017 w wersji 15,5. Narzędzie **dotnet-Svcutil** jako narzędzie .NET jest dostępne dla wielu platform w systemach Linux, MacOS i Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet — narzędzie Svcutil. XmlSerializer](dotnet-svcutil.xmlserializer-guide.md)

Na .NET Framework można wstępnie wygenerować zestaw serializacji za pomocą narzędzia Svcutil. Pakiet NuGet programu dotnet-Svcutil. XmlSerializer zapewnia podobną funkcjonalność w programie .NET Core. Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez <xref:System.Xml.Serialization.XmlSerializer>. Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak w przypadku [generatora serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework, [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest rozwiązaniem dla bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.
