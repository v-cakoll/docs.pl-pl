---
title: "Usługa: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 85e6dae6b8358799370079c52c3d04e7c3221b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="521ca-102">Usługa: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="521ca-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="521ca-103">Nazwa licznika: walidacji i uwierzytelniania błędów na sekundę.</span><span class="sxs-lookup"><span data-stu-id="521ca-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="521ca-104">Opis</span><span class="sxs-lookup"><span data-stu-id="521ca-104">Description</span></span>  
 <span data-ttu-id="521ca-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="521ca-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="521ca-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="521ca-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="521ca-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="521ca-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="521ca-108">Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="521ca-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="521ca-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).</span><span class="sxs-lookup"><span data-stu-id="521ca-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="521ca-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="521ca-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="521ca-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="521ca-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="521ca-112">Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="521ca-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="521ca-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="521ca-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="521ca-114">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły</span><span class="sxs-lookup"><span data-stu-id="521ca-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="521ca-115">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="521ca-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
