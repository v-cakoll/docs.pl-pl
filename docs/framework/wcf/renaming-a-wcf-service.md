---
title: Zmienianie nazwy usługi WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955145"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="1fb82-102">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1fb82-102">Renaming a WCF Service</span></span>
<span data-ttu-id="1fb82-103">W tym temacie opisano, jak można zmienić nazwy usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1fb82-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="1fb82-104">Zmienianie nazwy usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1fb82-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="1fb82-105">Wykonaj poniższe kroki, aby zmienić nazwy usługi w szablonie usługi Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="1fb82-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="1fb82-106">Zmień nazwę klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="1fb82-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="1fb82-107">W pliku konfiguracji usługi należy zmienić nazwy usługi na nową nazwę, które zostały wybrane, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1fb82-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="1fb82-108">Plik konfiguracji może być plik app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="1fb82-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="1fb82-109">Jeśli usługa jest webhosted, używa pliku \*.svc.</span><span class="sxs-lookup"><span data-stu-id="1fb82-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="1fb82-110">Otwórz plik svc i zmodyfikuj nazwę usługi, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1fb82-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="1fb82-111">Ten krok nie jest niezbędne do samodzielnie hostowanej aplikacji, ponieważ plik svc nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1fb82-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="1fb82-112">Zmiana nazwy kontraktu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="1fb82-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="1fb82-113">Wykonaj następujące kroki, aby zmienić nazwę kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="1fb82-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="1fb82-114">Zmień nazwę kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="1fb82-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="1fb82-115">W pliku konfiguracji usługi należy zmienić nazwy kontraktu usługi na nową nazwę, które zostały wybrane, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1fb82-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="1fb82-116">Plik konfiguracji może być plik app.config lub web.config, w zależności od modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="1fb82-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
