---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194052"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="e732c-102">Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="e732c-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="e732c-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="e732c-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="e732c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e732c-104">Description</span></span>  
 <span data-ttu-id="e732c-105">Ten licznik jest zwiększany, gdy komunikat zostanie odrzucony, ze względu na problem z zabezpieczeniami nie pasuje do żadnego licznika "Zabezpieczenia połączeń nie masz praw".</span><span class="sxs-lookup"><span data-stu-id="e732c-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="e732c-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="e732c-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="e732c-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e732c-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="e732c-108">Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="e732c-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="e732c-109">Weryfikacja podpisu nie powiodła się (komunikat został zmodyfikowany).</span><span class="sxs-lookup"><span data-stu-id="e732c-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="e732c-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas ataku powtarzania.</span><span class="sxs-lookup"><span data-stu-id="e732c-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="e732c-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="e732c-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="e732c-112">Komunikat brakuje niektórych wymaganych elementów (Brak znacznika czasu lub zaszyfrowanego bloku danych).</span><span class="sxs-lookup"><span data-stu-id="e732c-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="e732c-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="e732c-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
