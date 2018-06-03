---
title: Dodatkowe narzędzia .NET core
description: Przegląd dodatkowe narzędzia, które obsługują i rozszerzenia funkcji .NET Core.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: a842224a76962a9d6db820149a75f1255204e9b7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728566"
---
# <a name="net-core-additional-tools"></a>Dodatkowe narzędzia .NET core

W tej sekcji kompiluje listę narzędzi, które obsługują i rozszerzanie funkcji .NET Core, oprócz [.NET Core interfejsu wiersza polecenia (CLI)](..\tools\index.md) narzędzia.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzie odwołania do usługi sieci Web WCF](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF (Windows Communication Foundation) jest dostawcy podłączonej usługi Visual Studio, który zgłosił jego debut w [programu Visual Studio 2017 wersji 15,5 cala](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej, lub z pliku WSDL, a następnie generuje plik źródłowy jest zgodna z platformą .NET Core Definiowanie klasy serwera proxy usługi WCF z metod, które umożliwiają dostęp do operacji usługi sieci web.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[Narzędzia dotnet svcutil WCF](dotnet-svcutil-guide.md)

Narzędzia dotnet svcutil WCF (Windows Communication Foundation) jest narzędziem .NET Core interfejsu wiersza polecenia, które pobiera metadane z usługi sieci web w lokalizacji sieciowej lub z pliku WSDL, a następnie generuje plik źródłowy jest zgodna z platformą .NET Core definicji klasy serwera proxy usług WCF za pomocą metod Czy można uzyskać dostępu do operacji usługi sieci web. **Dotnet svcutil** narzędzie jest dostępna opcja alternatywnych [ **odwołania do usługi sieci Web WCF** ](/dotnet/core/additional-tools/wcf-web-service-reference-guide) programu Visual Studio połączenia dostawcy usług, który po raz pierwszy zostały wydane z programem Visual Studio v15.5 2017 r. **Dotnet svcutil** narzędzie jako narzędzie .NET Core interfejsu wiersza polecenia, jest dostępny i platform w systemie Linux, macOS i systemu Windows.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) rozwiązanie do bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie poprawić wydajność uruchamiania serializacji XML podczas serializacji lub do serializacji obiektów typu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.