---
title: Modelowanie i mapowanie
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 81080c416fd18c51be6626cb70a23073e049051d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784007"
---
# <a name="modeling-and-mapping"></a>Modelowanie i mapowanie
W [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można zdefiniować modelu koncepcyjnego, model magazynu i mapowanie między tymi dwoma w taki sposób, która najlepiej odpowiada aplikacji. Narzędzia modelu danych jednostki w programie Visual Studio umożliwiają tworzenie. [pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z bazy danych lub graficzny model, a następnie zaktualizuj plik podczas zmiany bazy danych lub modelu.  
  
 Uruchamianie 4.1 Framework jednostki można również utworzyć programowo przy użyciu rozwiązania deweloperskiego Code First modelu. Istnieją dwa różne scenariusze dla rozwiązania deweloperskiego Code First. W obu przypadkach deweloper definiuje model zarządzanego, tworząc definicje klas .NET Framework, a następnie opcjonalnie określa dodatkowego mapowania lub konfiguracji przy użyciu adnotacji danych lub interfejsu API fluent.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Możesz również użyć Generator EDM, który jest dołączony do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, ssdl i MSL albo identyfikatorem plików na podstawie istniejącego źródła danych. Można też ręcznie utworzyć modelu i mapowania zawartości. Aby uzyskać więcej informacji, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
