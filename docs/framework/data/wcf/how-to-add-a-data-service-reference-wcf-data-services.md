---
title: 'Porady: Dodawanie odwołania usługi danych (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084640"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="de4ef-102">Porady: Dodawanie odwołania usługi danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="de4ef-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="de4ef-103">Możesz użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio, aby dodać odwołanie do usługi danych WCF.</span><span class="sxs-lookup"><span data-stu-id="de4ef-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="de4ef-104">Dzięki temu można łatwiej uzyskać dostęp do danych usługi w aplikacji klienckiej, który da się opracować w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="de4ef-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="de4ef-105">Po ukończeniu tej procedury klas danych są generowane na podstawie metadanych uzyskany z usługi danych.</span><span class="sxs-lookup"><span data-stu-id="de4ef-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="de4ef-106">Aby uzyskać więcej informacji, zobacz [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="de4ef-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="de4ef-107">Dodaj odwołanie do usługi danych</span><span class="sxs-lookup"><span data-stu-id="de4ef-107">Add a data service reference</span></span>

1. <span data-ttu-id="de4ef-108">(Opcjonalnie) Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i Zanotuj identyfikator URI usługi danych.</span><span class="sxs-lookup"><span data-stu-id="de4ef-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="de4ef-109">W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="de4ef-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="de4ef-110">Jeśli usługa danych jest częścią bieżącego rozwiązania, kliknij przycisk **odnajdź**.</span><span class="sxs-lookup"><span data-stu-id="de4ef-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="de4ef-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="de4ef-111">-or-</span></span>

     <span data-ttu-id="de4ef-112">W **adres** polu tekstowym wpisz podstawowy adres URL usługi danych, takich jak `http://localhost:1234/Northwind.svc`, a następnie kliknij przycisk **Przejdź**.</span><span class="sxs-lookup"><span data-stu-id="de4ef-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="de4ef-113">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="de4ef-113">Select **OK**.</span></span>

     <span data-ttu-id="de4ef-114">Nowy plik kodu, który zawiera klasy danych, które mogą uzyskać dostęp i korzystać z zasobów usługi danych zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="de4ef-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="de4ef-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de4ef-115">See also</span></span>

- [<span data-ttu-id="de4ef-116">Szybki start</span><span class="sxs-lookup"><span data-stu-id="de4ef-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)