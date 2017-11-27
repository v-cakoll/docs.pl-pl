---
title: "Błędy walidacji zabezpieczeń i uwierzytelniania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="f18ad-102">Błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="f18ad-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="f18ad-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="f18ad-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="f18ad-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f18ad-104">Description</span></span>  
 <span data-ttu-id="f18ad-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="f18ad-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="f18ad-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="f18ad-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="f18ad-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="f18ad-108">Token klienta nie powiodło się uwierzytelniania (na przykład nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="f18ad-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="f18ad-109">Weryfikacja podpisu nie powiodła się (na przykład wiadomości została naruszona).</span><span class="sxs-lookup"><span data-stu-id="f18ad-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="f18ad-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="f18ad-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="f18ad-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="f18ad-112">Niektóre elementy (na przykład brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="f18ad-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="f18ad-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
