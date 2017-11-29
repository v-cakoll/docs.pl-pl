---
title: "Zręczność kryptograficzna w zabezpieczeniach WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b07b23f4428053964fa33150c4300645242f918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="ffa02-102">Zręczność kryptograficzna w zabezpieczeniach WCF</span><span class="sxs-lookup"><span data-stu-id="ffa02-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="ffa02-103">W tym przykładzie pokazano, jak określić w algorytmie standard/niestandardowe do implementacji agile kryptograficznych w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="ffa02-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="ffa02-104">Próbka składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="ffa02-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="ffa02-105">Usługa</span><span class="sxs-lookup"><span data-stu-id="ffa02-105">Service</span></span>  
 <span data-ttu-id="ffa02-106">To jest hostowany na własnym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa, która implementuje `ICalculator` interfejsu i zabezpiecza punktu końcowego za pomocą <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z bezpiecznej sesji i niezawodnej sesji wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ffa02-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="ffa02-107">Usługa definiuje niestandardowego `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ffa02-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="ffa02-108">Klient</span><span class="sxs-lookup"><span data-stu-id="ffa02-108">Client</span></span>  
 <span data-ttu-id="ffa02-109">Jest to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klienta, który uzyskuje dostęp do usługi, po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="ffa02-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="ffa02-110">Wywołuje operacji udostępnianych przez `ICalculator` interfejsu i zaimplementowanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ffa02-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="ffa02-111">Klient również definiuje niestandardowe tej samej `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ffa02-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="ffa02-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ffa02-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="ffa02-113">Otwórz rozwiązanie CryptoAgility.sln w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ffa02-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="ffa02-114">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ffa02-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="ffa02-115">Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik service.exe z uprawnieniami administratora, klikając prawym przyciskiem myszy service.exe i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="ffa02-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="ffa02-116">Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin i uruchom plik client.exe normalnie.</span><span class="sxs-lookup"><span data-stu-id="ffa02-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffa02-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ffa02-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ffa02-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ffa02-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ffa02-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ffa02-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ffa02-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ffa02-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="ffa02-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffa02-121">See Also</span></span>  
 [<span data-ttu-id="ffa02-122">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ffa02-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
