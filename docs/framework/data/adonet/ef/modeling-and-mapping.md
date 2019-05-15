---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 55fea170d98c737197d1e3e26c8d25fd97760ddd
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583579"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
W [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można zdefiniować modelu koncepcyjnego, model magazynu i mapowanie między tymi dwoma w taki sposób, która najlepiej odpowiada aplikacji. Narzędzia modelu danych jednostki w programie Visual Studio umożliwiają tworzenie. [pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z bazy danych lub graficzny model, a następnie zaktualizuj plik podczas zmiany bazy danych lub modelu.  
  
 Uruchamianie 4.1 Framework jednostki można również utworzyć programowo przy użyciu rozwiązania deweloperskiego Code First modelu. Istnieją dwa różne scenariusze dla rozwiązania deweloperskiego Code First. W obu przypadkach deweloper definiuje model zarządzanego, tworząc definicje klas .NET Framework, a następnie opcjonalnie określa dodatkowego mapowania lub konfiguracji przy użyciu adnotacji danych lub interfejsu API fluent.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Można również użyć EDM Generator, który jest dołączony do programu .NET Framework. EdmGen.exe generuje .csdl, ssdl i MSL albo identyfikatorem plików na podstawie istniejącego źródła danych. Można też ręcznie utworzyć modelu i mapowania zawartości. Aby uzyskać więcej informacji, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
