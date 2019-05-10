---
title: 'Usługa: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 5843d25eb26bdd9facc324a2af50c6b02c5ad7c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613573"
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="bc41f-102">Usługa: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="bc41f-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="bc41f-103">Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="bc41f-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="bc41f-104">Opis</span><span class="sxs-lookup"><span data-stu-id="bc41f-104">Description</span></span>  
 <span data-ttu-id="bc41f-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="bc41f-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="bc41f-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="bc41f-106">Such problems include:</span></span>  
  
- <span data-ttu-id="bc41f-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="bc41f-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="bc41f-108">Token klienta nie powiodło się uwierzytelnianie (na przykład,, nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="bc41f-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
- <span data-ttu-id="bc41f-109">Weryfikacja podpisu nie powiodła się (na przykład,, wiadomości zostały zmodyfikowane).</span><span class="sxs-lookup"><span data-stu-id="bc41f-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
- <span data-ttu-id="bc41f-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="bc41f-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="bc41f-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="bc41f-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="bc41f-112">Niektóre wymagane elementy (na przykład,, brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bc41f-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="bc41f-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="bc41f-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
