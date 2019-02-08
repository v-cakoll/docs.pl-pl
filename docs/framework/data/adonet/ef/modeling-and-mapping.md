---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828309"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
W [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można zdefiniować modelu koncepcyjnego, model magazynu i mapowanie między tymi dwoma w taki sposób, która najlepiej odpowiada aplikacji. Narzędzia modelu danych jednostki w programie Visual Studio umożliwiają tworzenie. [pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z bazy danych lub graficzny model, a następnie zaktualizuj plik podczas zmiany bazy danych lub modelu.  
  
 Uruchamianie 4.1 Framework jednostki można również utworzyć programowo przy użyciu rozwiązania deweloperskiego Code First modelu. Istnieją dwa różne scenariusze dla rozwiązania deweloperskiego Code First. W obu przypadkach deweloper definiuje model zarządzanego, tworząc definicje klas .NET Framework, a następnie opcjonalnie określa dodatkowego mapowania lub konfiguracji przy użyciu adnotacji danych lub interfejsu API fluent.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Możesz również użyć Generator EDM, który jest dołączony do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, ssdl i MSL albo identyfikatorem plików na podstawie istniejącego źródła danych. Można też ręcznie utworzyć modelu i mapowania zawartości. Aby uzyskać więcej informacji, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
