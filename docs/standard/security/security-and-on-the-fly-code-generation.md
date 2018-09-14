---
title: Zabezpieczenia i generowanie kodu na bieżąco
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512845"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="f9bb8-102">Zabezpieczenia i generowanie kodu na bieżąco</span><span class="sxs-lookup"><span data-stu-id="f9bb8-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="f9bb8-103">Niektóre biblioteki działają przez generowanie kodu i uruchomiania go do wykonania niektórych operacji do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="f9bb8-104">Podstawowy problem jest generowanie kodu w imieniu mniejszym zaufanemu kodowi i uruchamiając go na wyższe zaufania.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="f9bb8-105">Problem worsens, gdy obiekt wywołujący może mieć wpływ na generowanie kodu, więc należy upewnić się, którym generowany jest tylko kodu, które uważasz za bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="f9bb8-106">Musisz wiedzieć, dokładnie, jaki kod jest generowany przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="f9bb8-107">Oznacza to, że muszą mieć ścisłą kontrolą od żadnych wartości, które można uzyskać od użytkownika, są to ciągi ujęty w cudzysłów, (które powinny być wyjściowym, więc nie mogą zawierać elementy nieoczekiwany kod), identyfikatory, (które powinny być sprawdzane w celu sprawdzenia, czy są prawidłowe identyfikatory) lub cokolwiek innego.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="f9bb8-108">Identyfikatory może być niebezpieczne, ponieważ skompilowanego zestawu można zmodyfikować tak, aby jego identyfikatory zawierać otrzymano nieoczekiwany znaki, które prawdopodobnie będą tę kwestię nieco (chociaż rzadko jest to luka w zabezpieczeniach).</span><span class="sxs-lookup"><span data-stu-id="f9bb8-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="f9bb8-109">Zalecane jest, że generowanie kodu za pomocą odbicia emisji, co często pozwala uniknąć wielu z tych problemów.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="f9bb8-110">Podczas kompilowania kodu, należy rozważyć, czy jest jakiś sposób złośliwy program, można zmodyfikować go.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="f9bb8-111">Czy istnieje niewielki przedział czasu, przez który złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator odczyta go lub przed kod ładuje plik dll?</span><span class="sxs-lookup"><span data-stu-id="f9bb8-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="f9bb8-112">Jeśli tak, należy włączyć ochronę do katalogu zawierającego te pliki za pomocą listy kontroli dostępu w systemie plików, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="f9bb8-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bb8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9bb8-113">See also</span></span>

- [<span data-ttu-id="f9bb8-114">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="f9bb8-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
