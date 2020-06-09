---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580440"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="13edf-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="13edf-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="13edf-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="13edf-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="13edf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="13edf-104">Description</span></span>  
 <span data-ttu-id="13edf-105">Komunikat został zamknięty ponownie.</span><span class="sxs-lookup"><span data-stu-id="13edf-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="13edf-106">Komunikat powinien być zamknięty tylko raz.</span><span class="sxs-lookup"><span data-stu-id="13edf-106">A message should be closed only once.</span></span> <span data-ttu-id="13edf-107">Jeśli ślad jest emitowany w kodzie rozszerzenia użytkownika, oznacza to, że kod rozszerzenia użytkownika zamyka komunikat, który został już zamknięty.</span><span class="sxs-lookup"><span data-stu-id="13edf-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="13edf-108">Jeśli ślad jest emitowany za pomocą kodu produktu, oznacza to, że kod rozszerzenia użytkownika może potencjalnie zamknąć komunikat zbyt wcześnie.</span><span class="sxs-lookup"><span data-stu-id="13edf-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13edf-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13edf-109">See also</span></span>

- [<span data-ttu-id="13edf-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="13edf-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="13edf-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="13edf-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="13edf-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="13edf-112">Administration and Diagnostics</span></span>](../index.md)
