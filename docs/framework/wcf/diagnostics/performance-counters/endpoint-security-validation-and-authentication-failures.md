---
title: 'Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8c46354fac11f5f0b46ef1b5629157f6da455fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="44bf6-102">Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="44bf6-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="44bf6-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="44bf6-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="44bf6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="44bf6-104">Description</span></span>  
 <span data-ttu-id="44bf6-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="44bf6-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="44bf6-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="44bf6-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="44bf6-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="44bf6-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="44bf6-108">Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="44bf6-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="44bf6-109">Weryfikacja podpisu nie powiodła się (wiadomość została naruszona).</span><span class="sxs-lookup"><span data-stu-id="44bf6-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="44bf6-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="44bf6-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="44bf6-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="44bf6-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="44bf6-112">Komunikat brakuje niektórych wymaganych elementów (brak sygnatury czasowej lub blok zaszyfrowanych danych).</span><span class="sxs-lookup"><span data-stu-id="44bf6-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="44bf6-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="44bf6-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
