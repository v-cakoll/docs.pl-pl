---
title: Dodatkowe narzędzia .NET core
description: Przegląd dodatkowe narzędzia, które obsługują i rozszerzenia funkcji .NET Core.
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: 2e33cdbcbe9c81e6c3af84f8f2795ee3dc6e28ae
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="abbe1-103">Dodatkowe narzędzia .NET core</span><span class="sxs-lookup"><span data-stu-id="abbe1-103">.NET Core additional tools</span></span>

<span data-ttu-id="abbe1-104">W tej sekcji kompiluje listę narzędzi, które obsługują i rozszerzanie funkcji .NET Core, oprócz [.NET Core interfejsu wiersza polecenia (CLI)](..\tools\index.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="abbe1-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="abbe1-105">Narzędzia odwołanie do usługi sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="abbe1-105">WCF Web Service Reference Tool</span></span>](wcf-web-service-reference-guide.md)

<span data-ttu-id="abbe1-106">Odwołanie do usługi sieci Web WCF jest dostawcy podłączonej usługi Visual Studio, który zgłosił jego debut w [programu Visual Studio 2017 wersji 15,5 cala](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span><span class="sxs-lookup"><span data-stu-id="abbe1-106">The WCF Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="abbe1-107">To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej, lub z pliku WSDL i generuje plik zgodnego źródła .NET Core zawierające kod serwera proxy klienta usługi Windows Communication Foundation (WCF) używanego do dostępu do sieci web Usługa.</span><span class="sxs-lookup"><span data-stu-id="abbe1-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[<span data-ttu-id="abbe1-108">Generator serializatora XML</span><span class="sxs-lookup"><span data-stu-id="abbe1-108">XML Serializer Generator</span></span>](xml-serializer-generator.md)

<span data-ttu-id="abbe1-109">Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) rozwiązanie do bibliotek .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="abbe1-109">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="abbe1-110">Tworzy zestaw serializacji XML dla typów zawartych w zestawie poprawić wydajność uruchamiania serializacji XML podczas serializacji lub do serializacji obiektów typu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="abbe1-110">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>