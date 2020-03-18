---
title: Zabezpieczenia i generowanie kodu na bieżąco
description: Generowanie kodu w imieniu kodu mniejszego zaufania, który działa przy wyższym zaufaniu, jest problemem zabezpieczeń, szczególnie wtedy, gdy obiekt wywołujący może wpływać na generowanie kodu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186801"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="08750-103">Zabezpieczenia i generowanie kodu na bieżąco</span><span class="sxs-lookup"><span data-stu-id="08750-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="08750-104">Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="08750-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="08750-105">Podstawowym problemem jest generowanie kodu w imieniu kodu mniejszego zaufania i uruchamianie go z większym zaufaniem.</span><span class="sxs-lookup"><span data-stu-id="08750-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="08750-106">Problem pogarsza się, gdy obiekt wywołujący może mieć wpływ na generowanie kodu, więc należy upewnić się, że generowany jest tylko kod, który uważasz za bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="08750-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="08750-107">Musisz dokładnie wiedzieć, jaki kod generujesz przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="08750-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="08750-108">Oznacza to, że musisz mieć ścisłe kontrole wszelkich wartości, które można uzyskać od użytkownika, czy to ciągi dołączone do cudzysłowu (które powinny być unikane, aby nie mogły zawierać nieoczekiwanych elementów kodu), identyfikatory (które powinny być sprawdzane, aby sprawdzić, czy są prawidłowe identyfikatorów) lub czegokolwiek innego.</span><span class="sxs-lookup"><span data-stu-id="08750-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="08750-109">Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw może być modyfikowany tak, aby jego identyfikatory zawierały dziwne znaki, które prawdopodobnie go złamią (chociaż rzadko jest to luka w zabezpieczeniach).</span><span class="sxs-lookup"><span data-stu-id="08750-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="08750-110">Zaleca się generowanie kodu z emitują odbicia, co często pomaga uniknąć wielu z tych problemów.</span><span class="sxs-lookup"><span data-stu-id="08750-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="08750-111">Podczas kompilowania kodu należy rozważyć, czy istnieje jakiś sposób, w jaki złośliwy program może go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="08750-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="08750-112">Czy istnieje małe okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku przed kompilatorem odczytuje go lub przed załadowaniem kodu pliku dll?</span><span class="sxs-lookup"><span data-stu-id="08750-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="08750-113">Jeśli tak, należy chronić katalog zawierający te pliki, przy użyciu listy kontroli dostępu w systemie plików, w stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="08750-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08750-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08750-114">See also</span></span>

- [<span data-ttu-id="08750-115">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="08750-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
