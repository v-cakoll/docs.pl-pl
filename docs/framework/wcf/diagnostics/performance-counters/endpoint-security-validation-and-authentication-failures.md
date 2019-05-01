---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: e69549a276e2f9cece966dd44f6a1b3a3d3cb59f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916334"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="c09da-102">Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="c09da-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="c09da-103">Nazwa komputera: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="c09da-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="c09da-104">Opis</span><span class="sxs-lookup"><span data-stu-id="c09da-104">Description</span></span>  
 <span data-ttu-id="c09da-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="c09da-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c09da-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="c09da-106">Such problems include:</span></span>  
  
- <span data-ttu-id="c09da-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c09da-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="c09da-108">Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="c09da-108">Client token has failed authentication (bad password).</span></span>  
  
- <span data-ttu-id="c09da-109">Weryfikacja podpisu nie powiodła się (komunikat został zmodyfikowany).</span><span class="sxs-lookup"><span data-stu-id="c09da-109">Signature verification has failed (the message has been tampered).</span></span>  
  
- <span data-ttu-id="c09da-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="c09da-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="c09da-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="c09da-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="c09da-112">Komunikat brakuje niektórych wymaganych elementów (Brak znacznika czasu lub zaszyfrowanego bloku danych).</span><span class="sxs-lookup"><span data-stu-id="c09da-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="c09da-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="c09da-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
