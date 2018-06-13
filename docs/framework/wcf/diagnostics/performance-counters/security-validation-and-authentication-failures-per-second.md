---
title: Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e69dafaf2e415a0686594c4757bcf20dfd135944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473233"
---
# <a name="security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="49006-102">Niepowodzenia uwierzytelniania i walidacji zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="49006-102">Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="49006-103">Nazwa licznika: walidacji i uwierzytelniania błędów na sekundę.</span><span class="sxs-lookup"><span data-stu-id="49006-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49006-104">Opis</span><span class="sxs-lookup"><span data-stu-id="49006-104">Description</span></span>  
 <span data-ttu-id="49006-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="49006-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="49006-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="49006-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="49006-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="49006-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="49006-108">Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="49006-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="49006-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).</span><span class="sxs-lookup"><span data-stu-id="49006-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="49006-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="49006-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="49006-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="49006-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="49006-112">Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="49006-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="49006-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="49006-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="49006-114">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="49006-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="49006-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="49006-115">(N1-N0)/((D1-D0)/F)</span></span>
