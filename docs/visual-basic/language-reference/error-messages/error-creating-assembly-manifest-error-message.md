---
title: "Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="a1176-102">Wystąpił błąd podczas tworzenia manifestu zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="a1176-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="a1176-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołuje konsolidator zestawów (znanej także jako Alink Al.exe), można wygenerować zestawu z manifestu.</span><span class="sxs-lookup"><span data-stu-id="a1176-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="a1176-104">Konsolidator zgłosił błąd w fazie emisji wstępnego tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1176-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="a1176-105">Może to występować, jeśli występują problemy z pliku klucza lub kontener klucza określony.</span><span class="sxs-lookup"><span data-stu-id="a1176-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="a1176-106">Pełni podpisać zestawu, należy podać prawidłowy plik klucza, który zawiera informacje o klucze publiczne i prywatne.</span><span class="sxs-lookup"><span data-stu-id="a1176-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="a1176-107">Aby opóźnić Podpisz zestaw, musisz wybrać **opóźnienie tylko znak** pole wyboru i podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym.</span><span class="sxs-lookup"><span data-stu-id="a1176-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="a1176-108">Klucz prywatny nie jest konieczne, gdy zestaw jest podpisywany z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="a1176-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="a1176-109">Aby uzyskać więcej informacji, zobacz [porady: podpisać zestawu (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span><span class="sxs-lookup"><span data-stu-id="a1176-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="a1176-110">**Identyfikator błędu:** BC30140</span><span class="sxs-lookup"><span data-stu-id="a1176-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a1176-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a1176-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="a1176-112">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe narzędzia błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) błąd AL1019 bardziej wyjaśnienie i porady</span><span class="sxs-lookup"><span data-stu-id="a1176-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="a1176-113">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a1176-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1176-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1176-114">See Also</span></span>  
 [<span data-ttu-id="a1176-115">Porady: podpisać zestawu (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a1176-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="a1176-116">Strona podpisywania, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="a1176-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="a1176-117">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="a1176-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="a1176-118">Narzędzie Al.exe błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="a1176-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="a1176-119">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="a1176-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
