---
title: Błędy walidacji zabezpieczeń i uwierzytelniania
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d7964c59f28f33d6ec7bc3ba605b84e6a201b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="02cce-102">Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="02cce-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="02cce-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="02cce-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="02cce-104">Opis</span><span class="sxs-lookup"><span data-stu-id="02cce-104">Description</span></span>  
 <span data-ttu-id="02cce-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="02cce-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="02cce-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="02cce-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="02cce-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="02cce-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="02cce-108">Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="02cce-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="02cce-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).</span><span class="sxs-lookup"><span data-stu-id="02cce-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="02cce-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="02cce-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="02cce-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="02cce-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="02cce-112">Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="02cce-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="02cce-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="02cce-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
