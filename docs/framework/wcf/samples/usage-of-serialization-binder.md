---
title: "Używanie obiektu wiążącego serializacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77f5c2914051c4310102a57b7181333bab6811b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="4116c-102">Używanie obiektu wiążącego serializacji</span><span class="sxs-lookup"><span data-stu-id="4116c-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="4116c-103">Ten przykład przedstawia sposób użycia <xref:System.Runtime.Serialization.SerializationBinder> Aby zmienić wersję typu ogólnego, gdy jest on serializowany.</span><span class="sxs-lookup"><span data-stu-id="4116c-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4116c-104">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="4116c-104">Demonstrates</span></span>  
 <span data-ttu-id="4116c-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="4116c-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4116c-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4116c-106">Discussion</span></span>  
 <span data-ttu-id="4116c-107">W tym przykładzie pokazano, jak dwie jednostki, które są przeznaczonych dla różnych wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] może komunikować się za pomocą binarnego elementu formatującego i wiążącego serializacji.</span><span class="sxs-lookup"><span data-stu-id="4116c-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="4116c-108">Rozwój tego przykładu zostały wykonane przy użyciu funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="4116c-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="4116c-109">Próbka składa się z serwerem przeznaczonych dla [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], który implementuje kontrakt typy ogólne i dwóch różnych klientów, co przeznaczonych dla [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] i przeznaczonych dla innej [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4116c-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="4116c-110">Dołącza serwera <xref:System.Runtime.Serialization.SerializationBinder> do binarne programu formatującego, aby można było zmienić wersję typy odpowiednio na serializacji, więc obaj klienci może wykonywać deserializację typu poprawnie.</span><span class="sxs-lookup"><span data-stu-id="4116c-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4116c-111">Aby skonfigurować, tworzenie i uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="4116c-111">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="4116c-112">Do wykonania klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (projekty 6), a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4116c-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4116c-113">W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie wybierz pozycję **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="4116c-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="4116c-114">Wybierz **serwera** pierwszy, a następnie **Client20** , a następnie **Client40**.</span><span class="sxs-lookup"><span data-stu-id="4116c-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="4116c-115">Wybierz **Start** działania te trzy projekty i pozostawić rest ustawioną **Brak**.</span><span class="sxs-lookup"><span data-stu-id="4116c-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4.  <span data-ttu-id="4116c-116">Kliknij przycisk **OK** , a następnie naciśnij klawisz F5, aby uruchomić próbki.</span><span class="sxs-lookup"><span data-stu-id="4116c-116">Click **OK** and then press F5 to run the sample.</span></span>
