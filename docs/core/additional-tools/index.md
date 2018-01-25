---
title: "Dodatkowe narzędzia .NET core"
description: "Przegląd dodatkowe narzędzia, które obsługują i rozszerzenia funkcji .NET Core."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 21fcc1190ee4586a8d7eb6fb8d63a7c312e63825
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2018
---
# <a name="net-core-additional-tools"></a>Dodatkowe narzędzia .NET core

W tej sekcji kompiluje listę narzędzi, które obsługują i rozszerzanie funkcji .NET Core, oprócz [.NET Core interfejsu wiersza polecenia (CLI)](..\tools\index.md) narzędzia.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[Narzędzia odwołanie do usługi sieci Web WCF](wcf-web-service-reference-guide.md)

Odwołanie do usługi sieci Web WCF jest dostawcy podłączonej usługi Visual Studio, który zgłosił jego debut w [programu Visual Studio 2017 wersji 15,5 cala](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej, lub z pliku WSDL i generuje plik zgodnego źródła .NET Core zawierające kod serwera proxy klienta usługi Windows Communication Foundation (WCF) używanego do dostępu do sieci web Usługa.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[Generator serializatora XML](xml-serializer-generator.md)

Podobnie jak [Generator serializatora Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) dla programu .NET Framework [pakietu Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) rozwiązanie do bibliotek .NET Core i .NET Standard. Tworzy zestaw serializacji XML dla typów zawartych w zestawie poprawić wydajność uruchamiania serializacji XML podczas serializacji lub do serializacji obiektów typu przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.