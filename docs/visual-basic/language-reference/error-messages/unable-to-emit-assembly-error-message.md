---
title: "Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="b3ed2-102">Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="b3ed2-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="b3ed2-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołania Assembly Linker (Al.exe, znanej także jako Alink) można wygenerować zestawu z manifestu, z konsolidatora raportowania błędów w fazie emisji tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="b3ed2-104">**Identyfikator błędu:** BC30145</span><span class="sxs-lookup"><span data-stu-id="b3ed2-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3ed2-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b3ed2-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="b3ed2-106">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe narzędzia błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) uzyskać dokładniejsze objaśnienie i porady.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="b3ed2-107">Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe (konsolidator zestawów)](https://msdn.microsoft.com/library/c405shex) lub [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="b3ed2-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="b3ed2-108">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="b3ed2-109">Aby ręcznie zarejestrować zestawu</span><span class="sxs-lookup"><span data-stu-id="b3ed2-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="b3ed2-110">Użyj [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23) można utworzyć pliku pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="b3ed2-111">Ten plik ma rozszerzenie .snk —.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="b3ed2-112">Usuń odwołania COM, który generuje błąd z projektu.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="b3ed2-113">Z systemu Windows **Start** menu wskaż **programy**, wskaż polecenie **Microsoft Visual Studio 2008**, wskaż polecenie **programu Visual Studio Tools**, i następnie kliknij przycisk **programu Visual Studio 2008 polecenie wiersza**.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="b3ed2-114">Przenieś do katalogu, w której chcesz umieścić Twojej otoki zestawu.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="b3ed2-115">Wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="b3ed2-116">Przykładem kodu, który może wprowadzić może być poniżej.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="b3ed2-117">Jeśli ścieżka lub plik zawiera spacje, użyj podwójny cudzysłów (").</span><span class="sxs-lookup"><span data-stu-id="b3ed2-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="b3ed2-118">W [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], Dodaj odwołanie do zestawu .NET do nowo utworzonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b3ed2-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ed2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3ed2-119">See Also</span></span>  
 [<span data-ttu-id="b3ed2-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="b3ed2-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="b3ed2-121">Narzędzie Al.exe błędy i ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="b3ed2-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="b3ed2-122">SN.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="b3ed2-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="b3ed2-123">Porady: tworzenie pary kluczy publiczno prywatnych</span><span class="sxs-lookup"><span data-stu-id="b3ed2-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="b3ed2-124">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="b3ed2-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
