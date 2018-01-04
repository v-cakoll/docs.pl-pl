---
title: Mapowanie i modelowania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a219e4e3a58e3bd3e71bab3d3c41c87c393b20da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modeling-and-mapping"></a>Mapowanie i modelowania
W [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można zdefiniować w modelu koncepcyjnym, modelu magazynu i mapowanie między nimi w taki sposób, który najlepiej pasujące do aplikacji. Narzędzi modelu danych jednostki w [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pozwalają tworzyć.[ Plik edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z bazy danych lub graficzny model, a następnie aktualizacji które plików podczas zmiany bazy danych lub modelu.  
  
 Uruchamianie 4.1 Framework jednostki można również utworzyć model programowo przy użyciu programowanie Code First. Istnieją dwa różne scenariusze dla rozwoju Code First. W obu przypadkach dewelopera definiuje model programowania definicje klas .NET Framework, a następnie opcjonalnie określa dodatkowe mapowania lub konfiguracji za pomocą adnotacji danych lub interfejsu API fluent.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](http://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Można również użyć generatora EDM, który jest dołączony do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje CSDL, ssdl i pliki MSL na podstawie istniejącego źródła danych. Można też ręcznie utworzyć modelu i mapowania zawartości. Aby uzyskać więcej informacji, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
