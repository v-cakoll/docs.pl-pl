---
title: Dodatkowe narzędzia
description: Omówienie dodatkowych narzędzi, które można zainstalować, które obsługują i poszerzają funkcje platformy .NET Core.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451528"
---
# <a name="net-core-additional-tools-overview"></a>Dodatkowe narzędzia platformy .NET Core — Omówienie

W tej sekcji została skompilowana lista narzędzi, które obsługują i poszerzają funkcje programu .NET Core, a także interfejs wiersza polecenia platformy .NET Core.

## <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie do dezinstalacji programu .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umożliwia wyczyszczenie zestawów .NET Core i środowiska uruchomieniowego w systemie, tak aby były nadal tylko określone wersje. Dostępna jest kolekcja opcji, aby określić, które wersje zostały odinstalowane.

## <a name="net-core-diagnostic-tools"></a>Narzędzia diagnostyczne platformy .NET Core

[dotnet-Counters](../diagnostics/dotnet-counters.md) to narzędzie do monitorowania wydajności służące do monitorowania kondycji pierwszego poziomu i badania wydajności.

mechanizm [dotnet-dump](../diagnostics/dotnet-dump.md) umożliwia zbieranie i analizowanie zrzutów podstawowych systemów Windows i Linux bez natywnego debugera.

Funkcja [monitorowania dotnet](../diagnostics/dotnet-trace.md) zbiera dane profilowania z aplikacji, które mogą pomóc w scenariuszach, w których należy się dowiedzieć, co powoduje powolne działanie aplikacji.

## <a name="wcf-web-service-reference-tool"></a>Narzędzie referencyjne usługi sieci Web WCF

[Narzędzie referencyjne usługi sieci Web](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) to Dostawca usługi połączonej z programu Visual Studio, który wykonał udostępnione w programie [Visual Studio 2017 w wersji 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). To narzędzie pobiera metadane z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub w pliku WSDL. Generuje plik źródłowy zgodny z platformą .NET Core, definiując klasę serwera proxy WCF przy użyciu metod, których można użyć w celu uzyskania dostępu do operacji usługi sieci Web.

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet — narzędzie Svcutil

Narzędzie WCF [dotnet-Svcutil](dotnet-svcutil-guide.md) jest narzędziem platformy .NET, które pobiera metadane z usługi sieci Web w lokalizacji sieciowej lub z pliku WSDL. Generuje plik źródłowy zgodny z platformą .NET Core, definiując klasę serwera proxy WCF przy użyciu metod, których można użyć w celu uzyskania dostępu do operacji usługi sieci Web.

Narzędzie **dotnet-Svcutil** jest alternatywą dla [**referencyjnej usługi sieci Web programu WCF**](wcf-web-service-reference-guide.md) , która jest dostarczana z programem Visual studio 2017 w wersji 15,5. Narzędzie **dotnet-Svcutil** jako narzędzie .NET jest dostępne w systemach Linux, MacOS i Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet — narzędzie Svcutil. XmlSerializer

Na .NET Framework można wstępnie wygenerować zestaw serializacji za pomocą narzędzia Svcutil. Narzędzie WCF [dotnet-Svcutil. XmlSerializer](dotnet-svcutil.xmlserializer-guide.md) oferuje podobną funkcjonalność w programie .NET Core. Wstępnie generuje C# kod serializacji dla typów w aplikacji klienckiej, które są używane przez kontrakt usługi WCF i który może zostać Zserializowany przez <xref:System.Xml.Serialization.XmlSerializer>. Poprawia to wydajność uruchomienia serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="xml-serializer-generator"></a>Generator serializatora XML

Podobnie jak w przypadku [generatora serializatorów XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework, [pakiet NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest rozwiązaniem dla bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność podczas uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.
