---
title: 'Instrukcje: Dodawanie odwołania do usługi danych (Usługi danych programu WCF)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790737"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="2706f-102">Instrukcje: Dodawanie odwołania do usługi danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="2706f-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="2706f-103">Aby dodać odwołanie do Usługi danych programu WCF, można użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2706f-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="2706f-104">Dzięki temu można łatwiej uzyskać dostęp do usługi danych w aplikacji klienckiej opracowywanej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2706f-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="2706f-105">Po wykonaniu tej procedury klasy danych są generowane na podstawie metadanych uzyskanych z usługi danych.</span><span class="sxs-lookup"><span data-stu-id="2706f-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="2706f-106">Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="2706f-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="2706f-107">Dodawanie odwołania do usługi danych</span><span class="sxs-lookup"><span data-stu-id="2706f-107">Add a data service reference</span></span>

1. <span data-ttu-id="2706f-108">Obowiązkowe Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i zanotuj identyfikator URI usługi danych.</span><span class="sxs-lookup"><span data-stu-id="2706f-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="2706f-109">W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz polecenie **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="2706f-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="2706f-110">Jeśli usługa danych jest częścią bieżącego rozwiązania, kliknij przycisk **odkryj**.</span><span class="sxs-lookup"><span data-stu-id="2706f-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="2706f-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="2706f-111">-or-</span></span>

     <span data-ttu-id="2706f-112">W polu tekstowym **adres** wpisz podstawowy adres URL usługi danych, `http://localhost:1234/Northwind.svc`na przykład, a następnie kliknij przycisk **Przejdź**.</span><span class="sxs-lookup"><span data-stu-id="2706f-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="2706f-113">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2706f-113">Select **OK**.</span></span>

     <span data-ttu-id="2706f-114">Nowy plik kodu, który zawiera klasy danych, które mogą uzyskiwać dostęp do zasobów usługi danych i współdziałać z nimi, jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="2706f-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="2706f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2706f-115">See also</span></span>

- [<span data-ttu-id="2706f-116">Szybki start</span><span class="sxs-lookup"><span data-stu-id="2706f-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
