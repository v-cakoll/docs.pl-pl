---
title: Zręczność kryptograficzna w zabezpieczeniach WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 40f4f8523d5286911216180846e94ec18e40da1c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="77267-102">Zręczność kryptograficzna w zabezpieczeniach WCF</span><span class="sxs-lookup"><span data-stu-id="77267-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="77267-103">W tym przykładzie pokazano, jak określić w algorytmie standard/niestandardowe do usług kryptograficznych agile implementacji klienta usługi Windows Communication Foundation (WCF) i usługi.</span><span class="sxs-lookup"><span data-stu-id="77267-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="77267-104">Próbka składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="77267-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="77267-105">Usługa</span><span class="sxs-lookup"><span data-stu-id="77267-105">Service</span></span>  
 <span data-ttu-id="77267-106">To jest samodzielnie hostowana usługa WCF, która implementuje `ICalculator` interfejsu i zabezpiecza punktu końcowego za pomocą <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z bezpiecznej sesji i niezawodnej sesji wyłączone.</span><span class="sxs-lookup"><span data-stu-id="77267-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="77267-107">Usługa definiuje niestandardowego `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="77267-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="77267-108">Klient</span><span class="sxs-lookup"><span data-stu-id="77267-108">Client</span></span>  
 <span data-ttu-id="77267-109">Jest to WCFclient, który uzyskuje dostęp do usługi, po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="77267-109">This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="77267-110">Wywołuje operacji udostępnianych przez `ICalculator` interfejsu i zaimplementowanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="77267-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="77267-111">Klient również definiuje niestandardowe tej samej `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="77267-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="77267-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="77267-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="77267-113">Otwórz rozwiązanie CryptoAgility.sln w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77267-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="77267-114">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="77267-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="77267-115">Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik service.exe z uprawnieniami administratora, klikając prawym przyciskiem myszy service.exe i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="77267-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="77267-116">Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin i uruchom plik client.exe normalnie.</span><span class="sxs-lookup"><span data-stu-id="77267-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77267-117">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="77267-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="77267-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="77267-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="77267-119">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="77267-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77267-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="77267-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="77267-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77267-121">See Also</span></span>  
 [<span data-ttu-id="77267-122">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="77267-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
