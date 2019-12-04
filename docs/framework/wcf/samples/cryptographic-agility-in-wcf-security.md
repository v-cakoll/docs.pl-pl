---
title: Elastyczność kryptograficzna w zabezpieczeniach WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714924"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="23f9a-102">Elastyczność kryptograficzna w zabezpieczeniach WCF</span><span class="sxs-lookup"><span data-stu-id="23f9a-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="23f9a-103">Ten przykład pokazuje, jak określić w algorytmie Standard/Custom, aby zapewnić kryptograficzną implementację Agile w ramach klienta i usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="23f9a-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="23f9a-104">Przykład składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="23f9a-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="23f9a-105">**Usługa**</span><span class="sxs-lookup"><span data-stu-id="23f9a-105">**Service**</span></span>

<span data-ttu-id="23f9a-106">Jest to samodzielna usługa WCF, która implementuje interfejs `ICalculator` i zabezpiecza punkt końcowy przy użyciu <xref:System.ServiceModel.WSHttpBinding> z obsługą bezpiecznej sesji i niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="23f9a-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="23f9a-107">Usługa definiuje niestandardową klasę `SecurityAlgorithmSuite`, aby określić algorytmy kryptograficzne, które mają być używane na potrzeby zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="23f9a-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="23f9a-108">**Klient**</span><span class="sxs-lookup"><span data-stu-id="23f9a-108">**Client**</span></span>

<span data-ttu-id="23f9a-109">Jest to klient WCF, który uzyskuje dostęp do usługi po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="23f9a-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="23f9a-110">Wywołuje operacje udostępniane przez interfejs `ICalculator` i implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="23f9a-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="23f9a-111">Klient definiuje również tę samą niestandardową klasę `SecurityAlgorithmSuite`, aby określić algorytmy kryptograficzne, które mają być używane na potrzeby zabezpieczeń komunikatów.</span><span class="sxs-lookup"><span data-stu-id="23f9a-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="23f9a-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="23f9a-112">To use this sample</span></span>

1. <span data-ttu-id="23f9a-113">Otwórz rozwiązanie CryptoAgility. sln w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="23f9a-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="23f9a-114">Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="23f9a-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="23f9a-115">Otwórz Eksploratora plików i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik Service. exe z uprawnieniami administratora, klikając prawym przyciskiem myszy pozycję Service. exe i wybierając polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="23f9a-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="23f9a-116">Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin i uruchom plik Client. exe normalnie.</span><span class="sxs-lookup"><span data-stu-id="23f9a-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23f9a-117">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="23f9a-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="23f9a-118">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="23f9a-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="23f9a-119">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23f9a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23f9a-120">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="23f9a-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="23f9a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f9a-121">See also</span></span>

- [<span data-ttu-id="23f9a-122">Zabezpieczenia Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="23f9a-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
