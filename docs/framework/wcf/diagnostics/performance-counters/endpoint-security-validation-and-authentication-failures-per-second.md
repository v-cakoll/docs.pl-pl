---
title: 'Punkt końcowy: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bc68f49326818f0e6687c06a38e5e51fd6960c9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="f4e83-102">Punkt końcowy: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="f4e83-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="f4e83-103">Nazwa licznika: walidacji i uwierzytelniania błędów na sekundę</span><span class="sxs-lookup"><span data-stu-id="f4e83-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="f4e83-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f4e83-104">Description</span></span>  
 <span data-ttu-id="f4e83-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="f4e83-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="f4e83-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="f4e83-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="f4e83-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f4e83-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="f4e83-108">Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="f4e83-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="f4e83-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).</span><span class="sxs-lookup"><span data-stu-id="f4e83-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="f4e83-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="f4e83-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="f4e83-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="f4e83-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="f4e83-112">Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f4e83-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="f4e83-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="f4e83-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="f4e83-114">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="f4e83-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="f4e83-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="f4e83-115">(N1-N0)/((D1-D0)/F)</span></span>
