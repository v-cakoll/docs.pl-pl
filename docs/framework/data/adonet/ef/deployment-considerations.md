---
title: Deployment Considerations (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: b240b7da1d05e1bf02e31acc3c99b16a908a6add
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689880"
---
# <a name="deployment-considerations-entity-framework"></a>Deployment Considerations (Entity Framework)
Ten temat zawiera informacje dotyczące wdrażania aplikacji, które używają ADO.NET Entity Framework, aby uzyskać dostęp do danych. Aby uzyskać więcej informacji na temat programu Entity Framework, zobacz [wprowadzenie](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework udostępnia zestaw narzędzi, integracja z usługą, które ułatwiają tworzenie w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia modelu danych jednostki ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). W tym temacie nie opisano sposobu korzystania z określonymi technologiami wdrożyć aplikację na podstawie platformy Entity Framework.  
  
 Visual Studio zawiera funkcje służące do dystrybuowania i wdrażania aplikacji, takich jak wdrażanie ClickOnce. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji i składników](/visualstudio/deployment/deploying-applications-services-and-components) w dokumentacji programu Visual Studio.  
  
 W przypadku wdrażania aplikacji, która używa programu Entity Framework, obowiązują następujące zastrzeżenia:  
  
-   Entity Framework jest składnikiem programu .NET Framework, począwszy od .NET Framework 3.5 Service Pack 1 (SP1). Należy upewnić się, że .NET Framework 3.5 z dodatkiem SP1 lub nowszej jest zainstalowane, podczas wdrażania aplikacji na podstawie platformy Entity Framework.  
  
-   Gdy model koncepcyjny jest generowany przez Kreator modelu Entity Data Model, ciąg połączenia jest tworzony w pliku konfiguracji aplikacji. Modelu i mapowania plików można osadzić jako zasobów aplikacji lub mogą być kopiowane do katalogu wyjściowego. Domyślnie są one wdrażane jako zasoby osadzonej aplikacji. Użyj `Metadata Artifact Processing` właściwość pliku Projektanta obiektów do wybrania jednej z tych opcji. Aby uzyskać więcej informacji, zobacz [jak: Kopiowanie modelu i mapowania plików do katalogu wyjściowego](https://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Upewnij się, że modelu i mapowania informacji (wyrażony w język definicji schematu koncepcyjnego (CSDL), język definicji schematu magazynu (SSDL) i mapowania specyfikacji języka (MSL)) jest wdrażany wraz z aplikacją, jak i w lokalizacji określona przez ciąg połączenia. Aby uzyskać więcej informacji, zobacz [parametry połączenia](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Osadzenie modelu i mapowania informacji jako zasobów aplikacji, należy ponownie skompilować i ponowne wdrażanie aplikacji za każdym razem, gdy model koncepcyjny jest aktualizowana.  
  
-   Ponieważ platforma Entity Framework jest składnikiem programu .NET Framework, można redystrybuować z aplikacją, zgodnie z umową licencyjną .NET Framework.  
  
## <a name="see-also"></a>Zobacz także
- [Program Entity Framework na platformie ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)
- [Projektowanie i zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
