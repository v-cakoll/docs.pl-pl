---
title: "Zabezpieczenia i generowanie kodu na bieżąco"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c00c66be812f2a1cdfdf761f681d2a0561a284bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="b0fc1-102">Zabezpieczenia i generowanie kodu na bieżąco</span><span class="sxs-lookup"><span data-stu-id="b0fc1-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="b0fc1-103">Działanie niektórych bibliotek, generowanie kodu i uruchomienie jej do wykonania niektórych operacji do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="b0fc1-104">Podstawowy problem jest generowanie kodu w imieniu mniejszym zaufania kodu i uruchomić je na wyższe zaufania.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="b0fc1-105">Problem worsens podczas wywołującego może mieć wpływ na generowanie kodu, dlatego należy upewnić się, że generowane jest tylko kod, który należy wziąć pod uwagę bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="b0fc1-106">Musisz wiedzieć, dokładnie jaki kod jest generowany przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="b0fc1-107">Oznacza to, że muszą mieć ścisłej kontroli na wartości, które można uzyskać od użytkownika, którymi są ujęte w cudzysłów ciągi (które należy zastosować ucieczkę, nie mogą zawierać elementy nieoczekiwany kod), identyfikatorów (które powinny być sprawdzane, aby sprawdzić, czy są one prawidłowe identyfikatory) lub innych elementów.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="b0fc1-108">Identyfikatory może być niebezpieczne, ponieważ może być modyfikowany skompilowanym zestawie, dzięki czemu jego identyfikatory zawierać dziwne znaki, które będą prawdopodobnie Podziel je (mimo że jest to rzadko luki w zabezpieczeniach).</span><span class="sxs-lookup"><span data-stu-id="b0fc1-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="b0fc1-109">Zaleca się, że generowanie kodu przy użyciu odbicia emisji, który często pomaga uniknąć wiele z tych problemów.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="b0fc1-110">Podczas kompilowania kodu rozważ, czy istnieje inny sposób złośliwych programów można go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="b0fc1-111">Czy istnieje krótkim przedziale czasu, w którym złośliwego kodu, można zmienić kod źródłowy na dysku przed kompilator odczytuje go lub przed kod ładuje plik dll?</span><span class="sxs-lookup"><span data-stu-id="b0fc1-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="b0fc1-112">Jeśli tak, należy chronić katalog zawierający pliki, za pomocą listy kontroli dostępu w systemie plików, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="b0fc1-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fc1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0fc1-113">See Also</span></span>  
 [<span data-ttu-id="b0fc1-114">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="b0fc1-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
