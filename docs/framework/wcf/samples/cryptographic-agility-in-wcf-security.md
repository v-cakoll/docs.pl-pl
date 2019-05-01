---
title: Zręczność kryptograficzna w zabezpieczeniach WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 64519e51b82780ce2b355251245d77bff0a9e73b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002212"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="ff900-102">Zręczność kryptograficzna w zabezpieczeniach WCF</span><span class="sxs-lookup"><span data-stu-id="ff900-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="ff900-103">Ten przykład pokazuje, jak określić w algorytmie standard/niestandardowa w celu zapewnienia implementację kryptografii agile klienta usługi Windows Communication Foundation (WCF) i usługi.</span><span class="sxs-lookup"><span data-stu-id="ff900-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="ff900-104">Przykład składa się z następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="ff900-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="ff900-105">**Usługa**</span><span class="sxs-lookup"><span data-stu-id="ff900-105">**Service**</span></span>

<span data-ttu-id="ff900-106">Jest to obsługiwanej samodzielnie usługi WCF, która implementuje `ICalculator` interfejs i zabezpiecza punktu końcowego za pomocą <xref:System.ServiceModel.WSHttpBinding> przy użyciu bezpiecznej sesji i niezawodnej sesji wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ff900-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="ff900-107">Usługa definiuje niestandardową `SecurityAlgorithmSuite` klasy, aby określić algorytmy kryptograficzne, które ma być używany do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ff900-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="ff900-108">**Klient**</span><span class="sxs-lookup"><span data-stu-id="ff900-108">**Client**</span></span>

<span data-ttu-id="ff900-109">Jest to klienta WCF, która uzyskuje dostęp do usługi po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="ff900-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="ff900-110">Wywołuje operacje udostępniane przez `ICalculator` interfejs i implementowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ff900-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="ff900-111">Klient definiuje również niestandardowe tego samego `SecurityAlgorithmSuite` klasy, aby określić algorytmy kryptograficzne, które ma być używany do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ff900-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="ff900-112">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ff900-112">To use this sample</span></span>

1. <span data-ttu-id="ff900-113">Otwórz rozwiązanie CryptoAgility.sln w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ff900-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="ff900-114">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="ff900-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="ff900-115">Otwórz [!INCLUDE[fileExplorer](~/includes/fileexplorer-md.md)] i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik service.exe z uprawnieniami administratora, kliknij prawym przyciskiem myszy service.exe i wybierając **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="ff900-115">Open [!INCLUDE[fileExplorer](~/includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="ff900-116">Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin, a następnie uruchom plik client.exe normalnie.</span><span class="sxs-lookup"><span data-stu-id="ff900-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff900-117">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ff900-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff900-118">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ff900-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ff900-119">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="ff900-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff900-120">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff900-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="ff900-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff900-121">See also</span></span>

- [<span data-ttu-id="ff900-122">Windows Communication Foundation zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ff900-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)