---
title: Błędy walidacji zabezpieczeń i uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 0f061e1e12321dbe8034d7619830f71717ca9d1f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664977"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="1fd64-102">Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="1fd64-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="1fd64-103">Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="1fd64-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="1fd64-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1fd64-104">Description</span></span>  
 <span data-ttu-id="1fd64-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="1fd64-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="1fd64-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="1fd64-106">Such problems include:</span></span>  
  
- <span data-ttu-id="1fd64-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1fd64-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="1fd64-108">Token klienta nie powiodło się uwierzytelnianie (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="1fd64-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="1fd64-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości zostały zmodyfikowane).</span><span class="sxs-lookup"><span data-stu-id="1fd64-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="1fd64-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="1fd64-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="1fd64-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="1fd64-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="1fd64-112">Niektóre wymagane elementy (na przykład brak sygnatur czasowych lub zaszyfrowanych danych, blokowanie) brakuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1fd64-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="1fd64-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="1fd64-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
