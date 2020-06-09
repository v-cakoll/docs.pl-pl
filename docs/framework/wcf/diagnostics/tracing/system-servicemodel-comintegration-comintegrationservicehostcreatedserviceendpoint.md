---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593753"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="a21a5-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="a21a5-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="a21a5-103">Nie można przenieść ani usunąć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a21a5-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a21a5-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a21a5-104">Description</span></span>  
 <span data-ttu-id="a21a5-105">Ślad wskazuje, że wystąpił błąd podczas próby przeniesienia, usunięcia lub odrzucenia komunikatu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a21a5-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="a21a5-106">Komunikaty usługi MSMQ są wykorzystywane przez Windows Communication Foundation (WCF) (gdy są używane z usługą Msmqbinding lub MsmqIntegrationBinding). Ten ślad jest powiązany z wybraną wartością `ReceiveErrorHandling` właściwości w usłudze msmqbinding lub MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="a21a5-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="a21a5-107">Ślad ten nie wskazuje ogólnego błędu systemu.</span><span class="sxs-lookup"><span data-stu-id="a21a5-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="a21a5-108">Oznacza to jednak, że dla komunikatu nie powiodła się Dyspozycja wybranego zatrucia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a21a5-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="a21a5-109">Aby uzyskać więcej informacji na temat sytuacji, w których komunikaty stają się trujące i jak skonfigurować usługę do odpowiednich potrzeb, zobacz [Obsługa komunikatów trujących](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="a21a5-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a21a5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a21a5-110">See also</span></span>

- [<span data-ttu-id="a21a5-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a21a5-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="a21a5-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="a21a5-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a21a5-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a21a5-113">Administration and Diagnostics</span></span>](../index.md)
