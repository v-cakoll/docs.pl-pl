---
title: 'Usługa: Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: 97752fbd4ff38c40917c132fddfe3798a7ee6766
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998325"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="37107-102">Usługa: Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="37107-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="37107-103">Nazwa komputera: Niepowodzenia uwierzytelniania na sekundę i weryfikacji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="37107-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="37107-104">Opis</span><span class="sxs-lookup"><span data-stu-id="37107-104">Description</span></span>  
 <span data-ttu-id="37107-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="37107-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="37107-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="37107-106">Such problems include:</span></span>  
  
- <span data-ttu-id="37107-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="37107-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="37107-108">Token klienta nie powiodło się uwierzytelnianie (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="37107-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="37107-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości zostały zmodyfikowane).</span><span class="sxs-lookup"><span data-stu-id="37107-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="37107-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="37107-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="37107-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="37107-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="37107-112">Niektóre wymagane elementy (na przykład brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="37107-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="37107-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="37107-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="37107-114">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły</span><span class="sxs-lookup"><span data-stu-id="37107-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="37107-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="37107-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
