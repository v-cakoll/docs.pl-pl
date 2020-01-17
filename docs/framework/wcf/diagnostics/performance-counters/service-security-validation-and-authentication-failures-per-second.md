---
title: 'Usługa: Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 4af18009-e778-490b-9ba6-e76485285830
ms.openlocfilehash: f3f27100afb7390a68d99421cad6f43d9abaccd5
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163868"
---
# <a name="service-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="c35cc-102">Usługa: Niepowodzenia uwierzytelniania i weryfikacji zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="c35cc-102">Service: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="c35cc-103">Nazwa licznika: Błędy walidacji zabezpieczeń i uwierzytelniania na sekundę.</span><span class="sxs-lookup"><span data-stu-id="c35cc-103">Counter name: Security Validation and Authentication Failures Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c35cc-104">Opis</span><span class="sxs-lookup"><span data-stu-id="c35cc-104">Description</span></span>  
 <span data-ttu-id="c35cc-105">Ten licznik jest zwiększany za każdym razem, gdy komunikat zostanie odrzucony z powodu problemu z zabezpieczeniami, którego nie dotyczy licznik "wywołania zabezpieczeń bez autoryzacji".</span><span class="sxs-lookup"><span data-stu-id="c35cc-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c35cc-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="c35cc-106">Such problems include:</span></span>  
  
- <span data-ttu-id="c35cc-107">Nie można odczytać z komunikatu tokenu klienta.</span><span class="sxs-lookup"><span data-stu-id="c35cc-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="c35cc-108">Uwierzytelnianie tokenu klienta nie powiodło się (na przykład złe hasło).</span><span class="sxs-lookup"><span data-stu-id="c35cc-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="c35cc-109">Weryfikacja podpisu nie powiodła się (na przykład komunikat został naruszony).</span><span class="sxs-lookup"><span data-stu-id="c35cc-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="c35cc-110">Komunikat jest duplikatem z poprzedniego, który może wystąpić podczas ataku metodą powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="c35cc-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="c35cc-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="c35cc-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="c35cc-112">W komunikacie brakuje niektórych wymaganych elementów (na przykład braku sygnatury czasowej lub zaszyfrowanego bloku danych).</span><span class="sxs-lookup"><span data-stu-id="c35cc-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="c35cc-113">Wystąpiły błędy podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="c35cc-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="c35cc-114">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="c35cc-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula,</span></span>  
  
 <span data-ttu-id="c35cc-115">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="c35cc-115">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
