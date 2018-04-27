---
title: 'Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61a5c6b753b8aa70905027bc1449739769cd8da5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="790dc-102">Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="790dc-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="790dc-103">Kompilator Visual Basic wywołania Assembly Linker (Al.exe, znanej także jako Alink) można wygenerować zestawu z manifestu, z konsolidatora raportowania błędów w fazie emisji tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="790dc-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="790dc-104">**Identyfikator błędu:** BC30145</span><span class="sxs-lookup"><span data-stu-id="790dc-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="790dc-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="790dc-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="790dc-106">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="790dc-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="790dc-107">Aby uzyskać dokładniejsze objaśnienie i porady.</span><span class="sxs-lookup"><span data-stu-id="790dc-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="790dc-108">Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) lub [Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="790dc-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="790dc-109">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="790dc-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="790dc-110">Aby ręcznie zarejestrować zestawu</span><span class="sxs-lookup"><span data-stu-id="790dc-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="790dc-111">Użyj [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)) do utworzenia pliku pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="790dc-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="790dc-112">Ten plik ma rozszerzenie .snk —.</span><span class="sxs-lookup"><span data-stu-id="790dc-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="790dc-113">Usuń odwołania COM, który generuje błąd z projektu.</span><span class="sxs-lookup"><span data-stu-id="790dc-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="790dc-114">Z systemu Windows **Start** menu wskaż **programy**, wskaż polecenie **Microsoft Visual Studio 2008**, wskaż polecenie **programu Visual Studio Tools**, i następnie kliknij przycisk **programu Visual Studio 2008 polecenie wiersza**.</span><span class="sxs-lookup"><span data-stu-id="790dc-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="790dc-115">Przenieś do katalogu, w której chcesz umieścić Twojej otoki zestawu.</span><span class="sxs-lookup"><span data-stu-id="790dc-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="790dc-116">Wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="790dc-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="790dc-117">Przykładem kodu, który może wprowadzić może być poniżej.</span><span class="sxs-lookup"><span data-stu-id="790dc-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="790dc-118">Jeśli ścieżka lub plik zawiera spacje, użyj podwójny cudzysłów (").</span><span class="sxs-lookup"><span data-stu-id="790dc-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="790dc-119">W [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], Dodaj odwołanie do zestawu .NET do nowo utworzonego pliku.</span><span class="sxs-lookup"><span data-stu-id="790dc-119">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="790dc-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="790dc-120">See Also</span></span>  
 
 <span data-ttu-id="790dc-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="790dc-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="790dc-122">[Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="790dc-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="790dc-123">Instrukcje: tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="790dc-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="790dc-124">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="790dc-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
