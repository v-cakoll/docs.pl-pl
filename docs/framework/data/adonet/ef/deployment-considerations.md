---
title: Zagadnienia dotyczące wdrażania (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 3e78fc413e50deda67aa8992179e500afa671f8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251612"
---
# <a name="deployment-considerations-entity-framework"></a>Zagadnienia dotyczące wdrażania (Entity Framework)
Ten temat zawiera informacje dotyczące wdrażania aplikacji, które używają Entity Framework ADO.NET do uzyskiwania dostępu do danych. Aby uzyskać więcej informacji na temat Entity Framework, zobacz [wprowadzenie](getting-started.md).  
  
 Entity Framework zawiera zestaw narzędzi, które integrują się z programem i ułatwiają tworzenie w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [narzędzia ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). W tym temacie nie opisano, jak używać określonych technologii do wdrażania aplikacji opartej na Entity Framework.  
  
 Program Visual Studio oferuje funkcje do dystrybuowania i wdrażania aplikacji, takich jak wdrażanie ClickOnce. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji i składników](/visualstudio/deployment/deploying-applications-services-and-components) w dokumentacji programu Visual Studio.  
  
 Podczas wdrażania aplikacji korzystającej z Entity Framework są stosowane następujące zagadnienia:  
  
- Entity Framework jest składnikiem .NET Framework, rozpoczynając od .NET Framework 3,5 z dodatkiem Service Pack 1 (SP1). Podczas wdrażania aplikacji opartej na Entity Framework należy upewnić się, że .NET Framework 3,5 SP1 lub nowsza wersja jest zainstalowana.  
  
- Po wygenerowaniu modelu koncepcyjnego za pomocą Kreatora Entity Data Model w pliku konfiguracji aplikacji zostanie utworzony ciąg połączenia. Pliki modelu i mapowania mogą być osadzane jako zasoby aplikacji lub mogą być kopiowane do katalogu wyjściowego. Domyślnie są one wdrażane jako osadzone zasoby aplikacji. `Metadata Artifact Processing` Użyj właściwości pliku Entity Designer, aby wybrać jedną z tych opcji. Aby uzyskać więcej informacji, zobacz [jak: Kopiuj model i Mapuj pliki do katalogu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100))wyjściowego.  
  
- Upewnij się, że informacje o modelu i mapowaniu (wyrażone w języku definicji schematu koncepcyjnego (CSDL), magazynu definicji schematu (SSDL) i języku specyfikacji mapowania (MSL) są wdrożone razem z aplikacją i w lokalizacji określone przez parametry połączenia. Aby uzyskać więcej informacji, zobacz [Parametry połączenia](connection-strings.md).  
  
- Podczas osadzania modelu i mapowania informacji jako zasobów aplikacji należy ponownie skompilować i wdrożyć aplikację za każdym razem, gdy model koncepcyjny zostanie zaktualizowany.  
  
- Ponieważ Entity Framework jest składnikiem .NET Framework, można go rozpowszechniać z aplikacją zgodnie z umową licencyjną .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](index.md)
- [Projektowanie i zagadnienia dotyczące wdrażania](development-and-deployment-considerations.md)
