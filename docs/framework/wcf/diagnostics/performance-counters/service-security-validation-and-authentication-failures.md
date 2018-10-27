---
title: 'Usługa: Błędy walidacji i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039994"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="804d6-102">Usługa: Błędy walidacji i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="804d6-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="804d6-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="804d6-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="804d6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="804d6-104">Description</span></span>  
 <span data-ttu-id="804d6-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="804d6-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="804d6-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="804d6-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="804d6-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="804d6-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="804d6-108">Token klienta nie powiodło się uwierzytelnianie (na przykład,, nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="804d6-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="804d6-109">Weryfikacja podpisu nie powiodła się (na przykład,, wiadomości zostały zmodyfikowane).</span><span class="sxs-lookup"><span data-stu-id="804d6-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="804d6-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="804d6-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="804d6-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="804d6-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="804d6-112">Niektóre wymagane elementy (na przykład,, brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="804d6-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="804d6-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="804d6-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
