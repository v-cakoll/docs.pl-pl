---
title: "Usługa: Błędy walidacji i uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 50944c55525150868e5ddac9730792c10f6b975c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="702c4-102">Usługa: Błędy walidacji i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="702c4-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="702c4-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="702c4-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="702c4-104">Opis</span><span class="sxs-lookup"><span data-stu-id="702c4-104">Description</span></span>  
 <span data-ttu-id="702c4-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="702c4-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="702c4-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="702c4-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="702c4-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="702c4-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="702c4-108">Token klienta nie powiodło się uwierzytelniania (na przykład,, nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="702c4-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="702c4-109">Weryfikacja podpisu nie powiodła się (na przykład, że wiadomość została naruszona).</span><span class="sxs-lookup"><span data-stu-id="702c4-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="702c4-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="702c4-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="702c4-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="702c4-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="702c4-112">Niektóre elementy (na przykład, brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="702c4-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="702c4-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="702c4-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
