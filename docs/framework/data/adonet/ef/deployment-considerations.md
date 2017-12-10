---
title: "Zagadnienia dotyczące wdrażania (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31f458f884bb7d1aad64657244e2e0278d713c20
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="deployment-considerations-entity-framework"></a>Zagadnienia dotyczące wdrażania (Entity Framework)
Ten temat zawiera informacje na temat wdrażania aplikacji, które używają programu Entity Framework ADO.NET dla dostępu do danych. Aby uzyskać więcej informacji na temat programu Entity Framework, zobacz [wprowadzenie](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework zapewnia zestaw narzędzi, które integrują się z i ułatwiają tworzenie w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzi modelu danych jednostki ADO.NET](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527). W tym temacie nie opisano sposobu używania określonych technologii do wdrażania aplikacji na podstawie programu Entity Framework.  
  
 Program Visual Studio udostępnia urządzenia do rozpowszechniania i wdrażanie aplikacji, takich jak wdrażanie technologii ClickOnce. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji i składników](/visualstudio/deployment/deploying-applications-services-and-components) w dokumentacji programu Visual Studio.  
  
 Poniższe zagadnienia do rozważenia podczas wdrażania aplikacji korzystającej z programu Entity Framework:  
  
-   Entity Framework jest składnikiem programu .NET Framework w programie .NET Framework 3.5 Service Pack 1 (SP1). Pamiętaj, że .NET Framework 3.5 z dodatkiem SP1 lub nowszy jest zainstalowany podczas wdrażania aplikacji na podstawie programu Entity Framework.  
  
-   Gdy model koncepcyjny jest generowany przez kreatora modelu danych jednostki, ciąg połączenia jest tworzony w pliku konfiguracyjnym aplikacji. Model i mapowania plików może być osadzony jako zasoby aplikacji lub mogą zostać skopiowane do katalogu wyjściowego. Domyślnie są wdrażane jako zasoby osadzone aplikacji. Użyj `Metadata Artifact Processing` właściwość pliku Entity Designer, aby wybrać jedną z następujących opcji. Aby uzyskać więcej informacji, zobacz [porady: kopiowanie modelu i mapowania plików do katalogu wyjściowego](http://msdn.microsoft.com/en-us/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Upewnij się, że model i mapowania informacji (wyrażony w schematu koncepcyjnego definition language (CSDL), języka definicji schematu magazynu (SSDL) i język specyfikacji mapowania (MSL)) jest wdrażany razem z aplikacji, jak i w lokalizacji określona przez ciąg połączenia. Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Osadzenie modelu i mapowania informacji jako zasoby aplikacji, należy ponownie skompilować i ponownie wdrożyć aplikację w każdej aktualizacji modelu koncepcyjnego.  
  
-   Ponieważ programu Entity Framework jest składnikiem programu .NET Framework, mogą być rozpowszechniane za pomocą aplikacji zgodnie z umową licencyjną .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Projektowanie i zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
