---
title: "Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="e5715-102">Punkt końcowy: Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="e5715-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="e5715-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="e5715-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="e5715-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e5715-104">Description</span></span>  
 <span data-ttu-id="e5715-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="e5715-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="e5715-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5715-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="e5715-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e5715-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="e5715-108">Token klienta nie powiodło się uwierzytelnianie (nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="e5715-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="e5715-109">Weryfikacja podpisu nie powiodła się (wiadomość została naruszona).</span><span class="sxs-lookup"><span data-stu-id="e5715-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="e5715-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="e5715-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="e5715-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="e5715-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="e5715-112">Komunikat brakuje niektórych wymaganych elementów (brak sygnatury czasowej lub blok zaszyfrowanych danych).</span><span class="sxs-lookup"><span data-stu-id="e5715-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="e5715-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="e5715-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
