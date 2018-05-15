---
title: 'Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 8f497069088ad30a3be58d02caa0a32f7f1b21b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="b72ef-102">Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;</span><span class="sxs-lookup"><span data-stu-id="b72ef-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="b72ef-103">Kompilator Visual Basic wywołania Assembly Linker (Al.exe, znanej także jako Alink) można wygenerować zestawu z manifestu, z konsolidatora raportowania błędów w fazie emisji tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="b72ef-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="b72ef-104">**Identyfikator błędu:** BC30145</span><span class="sxs-lookup"><span data-stu-id="b72ef-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b72ef-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b72ef-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="b72ef-106">Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="b72ef-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="b72ef-107">Aby uzyskać dokładniejsze objaśnienie i porady.</span><span class="sxs-lookup"><span data-stu-id="b72ef-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="b72ef-108">Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) lub [Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b72ef-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="b72ef-109">Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b72ef-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="b72ef-110">Aby ręcznie zarejestrować zestawu</span><span class="sxs-lookup"><span data-stu-id="b72ef-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="b72ef-111">Użyj [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)) do utworzenia pliku pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="b72ef-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="b72ef-112">Ten plik ma rozszerzenie .snk —.</span><span class="sxs-lookup"><span data-stu-id="b72ef-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="b72ef-113">Usuń odwołania COM, który generuje błąd z projektu.</span><span class="sxs-lookup"><span data-stu-id="b72ef-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="b72ef-114">Z systemu Windows **Start** menu wskaż **programy**, wskaż polecenie **Microsoft Visual Studio 2008**, wskaż polecenie **programu Visual Studio Tools**, i następnie kliknij przycisk **programu Visual Studio 2008 polecenie wiersza**.</span><span class="sxs-lookup"><span data-stu-id="b72ef-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="b72ef-115">Przenieś do katalogu, w której chcesz umieścić Twojej otoki zestawu.</span><span class="sxs-lookup"><span data-stu-id="b72ef-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="b72ef-116">Wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="b72ef-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="b72ef-117">Przykładem kodu, który może wprowadzić może być poniżej.</span><span class="sxs-lookup"><span data-stu-id="b72ef-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="b72ef-118">Jeśli ścieżka lub plik zawiera spacje, użyj podwójny cudzysłów (").</span><span class="sxs-lookup"><span data-stu-id="b72ef-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="b72ef-119">W programie Visual Studio Dodaj odwołanie do pliku, który właśnie utworzony zestaw .NET.</span><span class="sxs-lookup"><span data-stu-id="b72ef-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72ef-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b72ef-120">See Also</span></span>  
 
 <span data-ttu-id="b72ef-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="b72ef-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="b72ef-122">[Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="b72ef-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="b72ef-123">Instrukcje: tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="b72ef-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="b72ef-124">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="b72ef-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
