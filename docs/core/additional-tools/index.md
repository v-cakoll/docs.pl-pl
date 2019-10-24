---
title: Dodatkowe narzędzia interfejsu wiersza polecenia platformy .NET Core
description: Omówienie dodatkowych narzędzi, które można zainstalować, które obsługują i poszerzają funkcje platformy .NET Core.
author: mlacouture
ms.date: 11/27/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: c885d6f6b0417a80dd6e26afe9572766738c5b4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771967"
---
# <a name="net-core-additional-tools-overview"></a>Dodatkowe narzędzia platformy .NET Core — Omówienie

Ta sekcja zawiera kompilację listy narzędzi, które obsługują i poszerzają funkcje platformy .NET Core, a także narzędzia [interfejsu wiersza polecenia (CLI) platformy .NET Core](../tools/index.md) .

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzie referencyjne usługi sieci Web WCF](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF (Windows Communication Foundation) to Dostawca usługi połączonej z programu Visual Studio, który wykonał udostępnione w programie [Visual studio 2017 w wersji 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). To narzędzie umożliwia pobranie metadanych z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub w pliku WSDL, a następnie wygenerowanie pliku źródłowego zgodnego z platformą .NET Core, zdefiniowanie klasy serwera proxy WCF przy użyciu metod, których można użyć w celu uzyskania dostępu do operacji usługi sieci Web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet — narzędzie Svcutil](dotnet-svcutil-guide.md)

Narzędzie WCF (Windows Communication Foundation) dotnet-Svcutil to narzędzie interfejs wiersza polecenia platformy .NET Core, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL, i generuje plik źródłowy zgodny z platformą .NET Core, Definiowanie klasy serwera proxy WCF przy użyciu metod służy do uzyskiwania dostępu do operacji usługi sieci Web.
Narzędzie **dotnet-Svcutil** jest alternatywną opcją dla [**referencyjnej usługi sieci Web programu WCF**](wcf-web-service-reference-guide.md) , która jest dostarczana z programem Visual studio 2017 w wersji 15,5. Narzędzie **dotnet-Svcutil** jako narzędzie interfejs wiersza polecenia platformy .NET Core jest dostępne dla wielu platform w systemach Linux, MacOS i Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet — narzędzie Svcutil. XmlSerializer](dotnet-svcutil.xmlserializer-guide.md)

Na .NET Framework można wstępnie wygenerować zestaw serializacji za pomocą narzędzia Svcutil. Pakiet NuGet programu dotnet-Svcutil. XmlSerializer zapewnia podobną funkcjonalność w programie .NET Core. Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez <xref:System.Xml.Serialization.XmlSerializer>. Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak w przypadku [generatora serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework, [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest rozwiązaniem dla bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.
