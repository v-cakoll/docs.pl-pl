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
ms.openlocfilehash: 808c0d648043df6c5a3dda4646e45ba1492345a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-security-validation-and-authentication-failures"></a><span data-ttu-id="37230-102">Usługa: Błędy walidacji i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="37230-102">Service: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="37230-103">Nazwa licznika: błędy walidacji zabezpieczeń i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="37230-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="37230-104">Opis</span><span class="sxs-lookup"><span data-stu-id="37230-104">Description</span></span>  
 <span data-ttu-id="37230-105">Ten licznik jest zwiększany, gdy komunikat jest odrzucone z powodu problemu zabezpieczeń nie pasuje do żadnego licznika "Zabezpieczeń wywołań nieautoryzowane".</span><span class="sxs-lookup"><span data-stu-id="37230-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="37230-106">Takie problemy obejmują:</span><span class="sxs-lookup"><span data-stu-id="37230-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="37230-107">Nie można odczytać tokenu klienta z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="37230-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="37230-108">Token klienta nie powiodło się uwierzytelniania (na przykład,, nieprawidłowe hasło).</span><span class="sxs-lookup"><span data-stu-id="37230-108">Client token has failed authentication (for example,, bad password).</span></span>  
  
-   <span data-ttu-id="37230-109">Weryfikacja podpisu nie powiodła się (na przykład, że wiadomość została naruszona).</span><span class="sxs-lookup"><span data-stu-id="37230-109">Signature verification has failed (for example,, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="37230-110">Komunikat jest duplikatem z poprzedniej wersji, która może się zdarzyć podczas atakiem polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="37230-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="37230-111">Wystąpił błąd odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="37230-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="37230-112">Niektóre elementy (na przykład, brak sygnatury czasowej lub zaszyfrowanych danych, blokowanie) brakuje wymaganych z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="37230-112">Some required elements (for example,, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="37230-113">Wystąpił błąd podczas uzgadniania TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="37230-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
