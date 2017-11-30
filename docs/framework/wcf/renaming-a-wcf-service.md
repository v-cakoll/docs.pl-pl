---
title: "Zmienianie nazwy usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee707a898bf915491cc1ca44e0606c261dc87dc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="3fb0d-102">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="3fb0d-102">Renaming a WCF Service</span></span>
<span data-ttu-id="3fb0d-103">W tym temacie opisano, jak można zmienić nazwy [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="3fb0d-104">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="3fb0d-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="3fb0d-105">Wykonaj poniższe kroki, aby zmienić nazwę usługi w programie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] szablonu,</span><span class="sxs-lookup"><span data-stu-id="3fb0d-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="3fb0d-106">Zmień nazwę klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="3fb0d-107">W pliku konfiguracji usługi Zmień nazwę usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="3fb0d-108">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="3fb0d-109">Czy usługa jest webhosted, używa plik *.svc.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-109">If your service is webhosted, it uses an *.svc file.</span></span> <span data-ttu-id="3fb0d-110">Otwórz plik svc i zmodyfikować nazwę usługi, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="3fb0d-111">Ten krok nie jest konieczne własnym obsługiwanych aplikacji, ponieważ nie ma żadnego pliku svc.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="3fb0d-112">Zmiana nazwy kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="3fb0d-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="3fb0d-113">Wykonaj poniższe kroki, aby zmienić nazwę kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="3fb0d-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="3fb0d-114">Zmień nazwę kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="3fb0d-115">W pliku konfiguracji usługi należy zmienić nazwę kontraktu usługi na nową nazwę, którą wybrano, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="3fb0d-116">Może to być plik konfiguracji pliku app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="3fb0d-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
