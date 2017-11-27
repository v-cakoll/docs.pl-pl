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
ms.openlocfilehash: 2004b950f1096f574734259ba02944577dd9adc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="35847-102">Mapowanie i modelowania</span><span class="sxs-lookup"><span data-stu-id="35847-102">Modeling and Mapping</span></span>
<span data-ttu-id="35847-103">W [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można zdefiniować w modelu koncepcyjnym, modelu magazynu i mapowanie między nimi w taki sposób, który najlepiej pasujące do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35847-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="35847-104">Narzędzi modelu danych jednostki w [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pozwalają tworzyć.[ Plik edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z bazy danych lub graficzny model, a następnie aktualizacji które plików podczas zmiany bazy danych lub modelu.</span><span class="sxs-lookup"><span data-stu-id="35847-104">The Entity Data Model Tools in [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] allow you to create an .[edmx file](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="35847-105">Uruchamianie 4.1 Framework jednostki można również utworzyć model programowo przy użyciu programowanie Code First.</span><span class="sxs-lookup"><span data-stu-id="35847-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="35847-106">Istnieją dwa różne scenariusze dla rozwoju Code First.</span><span class="sxs-lookup"><span data-stu-id="35847-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="35847-107">W obu przypadkach dewelopera definiuje model programowania definicje klas .NET Framework, a następnie opcjonalnie określa dodatkowe mapowania lub konfiguracji za pomocą adnotacji danych lub interfejsu API fluent.</span><span class="sxs-lookup"><span data-stu-id="35847-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="35847-108">Aby uzyskać więcej informacji, zobacz [tworzenia i mapowania modelu koncepcyjnego](http://go.microsoft.com/fwlink/?LinkId=235016).</span><span class="sxs-lookup"><span data-stu-id="35847-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="35847-109">Można również użyć generatora EDM, który jest dołączony do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35847-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="35847-110">EdmGen.exe generuje CSDL, ssdl i pliki MSL na podstawie istniejącego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="35847-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="35847-111">Można też ręcznie utworzyć modelu i mapowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="35847-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="35847-112">Aby uzyskać więcej informacji, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="35847-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
