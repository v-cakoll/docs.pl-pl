---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: e69549a276e2f9cece966dd44f6a1b3a3d3cb59f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181098"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="6ff3e-102">Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="6ff3e-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="6ff3e-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="6ff3e-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="6ff3e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6ff3e-104">Description</span></span>  
 <span data-ttu-id="6ff3e-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="6ff3e-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="6ff3e-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="6ff3e-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="6ff3e-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="6ff3e-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="6ff3e-108">Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="6ff3e-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="6ff3e-109">Weryfikacja podpisu nie powiodła się (komunikat został zmodyfikowany).</span><span class="sxs-lookup"><span data-stu-id="6ff3e-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="6ff3e-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="6ff3e-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="6ff3e-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="6ff3e-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="6ff3e-112">Komunikat brakuje niektórych wymaganych elementów (Brak znacznika czasu lub zaszyfrowanego bloku danych).</span><span class="sxs-lookup"><span data-stu-id="6ff3e-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="6ff3e-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="6ff3e-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
