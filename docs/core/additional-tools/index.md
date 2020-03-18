---
title: Dodatkowe narzędzia
description: Omówienie dodatkowych narzędzi, które można zainstalować, które obsługują i rozszerzyć .NET Core funkcji.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451528"
---
# <a name="net-core-additional-tools-overview"></a>Omówienie dodatkowych narzędzi programu .NET Core

W tej sekcji skompilowano listę narzędzi obsługujących i rozszerzających funkcjonalność .NET Core, oprócz funkcji cli .NET Core.

## <a name="net-core-uninstall-tool"></a>Narzędzie do dezinstalacji platformy .NET Core

[Narzędzie .NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umożliwia czyszczenie zestawów SDK i runtimes .NET Core w systemie w taki sposób, że pozostają tylko określone wersje. Dostępna jest kolekcja opcji określających, które wersje są odinstalowane.

## <a name="net-core-diagnostic-tools"></a>Narzędzia diagnostyczne .NET Core

[dotnet-counters](../diagnostics/dotnet-counters.md) jest narzędziem do monitorowania wydajności do monitorowania kondycji pierwszego poziomu i badania wydajności.

[dotnet-dump](../diagnostics/dotnet-dump.md) umożliwia zbieranie i analizowanie zrzutów rdzenia systemu Windows i Linux bez natywnego debugera.

[dotnet-trace](../diagnostics/dotnet-trace.md) zbiera dane profilowania z aplikacji, które mogą pomóc w scenariuszach, w których należy dowiedzieć się, co powoduje, że aplikacja działa wolno.

## <a name="wcf-web-service-reference-tool"></a>Narzędzie Odwołanie do usługi sieci Web WCF

[Narzędzie Do odwoływania się do usług sieci Web](wcf-web-service-reference-guide.md) WCF (Windows Communication Foundation) jest dostawcą usług połączonych z programem Visual Studio, który zadebiutował w programie Visual Studio [2017 w wersji 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL. Generuje plik źródłowy zgodny z .NET Core, definiując klasę serwera proxy WCF z metodami, których można użyć do uzyskania dostępu do operacji usługi sieci web.

## <a name="wcf-dotnet-svcutil-tool"></a>Narzędzie WCF dotnet-svcutil

Narzędzie WCF [dotnet-svcutil](dotnet-svcutil-guide.md) jest narzędziem .NET, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL. Generuje plik źródłowy zgodny z .NET Core, definiując klasę serwera proxy WCF z metodami, których można użyć do uzyskania dostępu do operacji usługi sieci web.

Narzędzie **dotnet-svcutil** jest alternatywą dla dostawcy usług [**sieci Web WCF Visual**](wcf-web-service-reference-guide.md) Studio, który po raz pierwszy został dostarczony z programiem Visual Studio 2017 w wersji 15.5. Narzędzie **dotnet-svcutil** jako narzędzie .NET jest dostępne w systemach Linux, macOS i Windows.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>Narzędzie WCF dotnet-svcutil.xmlserializer

W platformie .NET Framework można wstępnie wygenerować zestaw serializacji za pomocą narzędzia svcutil. Narzędzie WCF [dotnet-svcutil.xmlserializer](dotnet-svcutil.xmlserializer-guide.md) zapewnia podobną funkcjonalność w .NET Core. Wstępnie generuje kod serializacji C# dla typów w aplikacji klienckiej, które są używane przez Umowę <xref:System.Xml.Serialization.XmlSerializer>serwisową WCF i które mogą być serializowane przez . Zwiększa to wydajność uruchamiania serializacji XML podczas serializacji lub deserializacji obiektów tych typów.

## <a name="xml-serializer-generator"></a>Generator serializatora XML

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework, [pakiet Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) jest rozwiązaniem dla bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie, aby zwiększyć wydajność uruchamiania serializacji XML podczas <xref:System.Xml.Serialization.XmlSerializer>serializacji lub deserializacji obiektów tych typów przy użyciu .
