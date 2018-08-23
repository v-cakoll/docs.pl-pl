---
title: 'Nie można wyemitować zestawu: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 404a8255adcdc414a40b40395ada1c90c1078325
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751934"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="a4e65-102">Nie można wyemitować zestawu: \<komunikat o błędzie ></span><span class="sxs-lookup"><span data-stu-id="a4e65-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="a4e65-103">Kompilator języka Visual Basic wywołuje Assembly Linker (*Al.exe*, znanego również jako Alink) do generowania zestawów z manifestu i konsolidator zgłasza błąd, na etapie emisji tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="a4e65-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="a4e65-104">**Identyfikator błędu:** BC30145</span><span class="sxs-lookup"><span data-stu-id="a4e65-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a4e65-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a4e65-105">To correct this error</span></span>

1. <span data-ttu-id="a4e65-106">Sprawdź komunikat o błędzie w cudzysłowach i zapoznaj się z tematem [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) uzyskać dokładniejsze objaśnienie i porady.</span><span class="sxs-lookup"><span data-stu-id="a4e65-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="a4e65-107">Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) lub [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="a4e65-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="a4e65-108">Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4e65-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="a4e65-109">Aby podpisać zestaw ręcznie</span><span class="sxs-lookup"><span data-stu-id="a4e65-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="a4e65-110">Użyj [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)) można utworzyć pliku pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="a4e65-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="a4e65-111">Ten plik zawiera *.snk* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a4e65-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="a4e65-112">Usuń odwołanie COM, który generuje błąd z projektu.</span><span class="sxs-lookup"><span data-stu-id="a4e65-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="a4e65-113">Otwórz [wiersz polecenia programisty dla programu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a4e65-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="a4e65-114">W systemie Windows 10, wprowadź **wiersz polecenia dla deweloperów** w polu wyszukiwania na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="a4e65-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="a4e65-115">Następnie wybierz **wiersz polecenia programisty dla programu VS 2017** z listy wyników.</span><span class="sxs-lookup"><span data-stu-id="a4e65-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="a4e65-116">Zmień katalog na katalog, w którym chcesz umieścić swoje otoki zestawu.</span><span class="sxs-lookup"><span data-stu-id="a4e65-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="a4e65-117">Wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a4e65-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="a4e65-118">Jest przykładem rzeczywiste polecenia, które możesz wprowadzić:</span><span class="sxs-lookup"><span data-stu-id="a4e65-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="a4e65-119">Jeśli pliku lub ścieżki zawiera spacje, należy użyć podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="a4e65-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="a4e65-120">W programie Visual Studio należy dodać odwołanie do zestawu .NET do pliku, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a4e65-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4e65-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4e65-121">See also</span></span>

- <span data-ttu-id="a4e65-122">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="a4e65-122">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>
- <span data-ttu-id="a4e65-123">[Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="a4e65-123">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
- [<span data-ttu-id="a4e65-124">Instrukcje: tworzenie pary kluczy publiczny-prywatny</span><span class="sxs-lookup"><span data-stu-id="a4e65-124">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="a4e65-125">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="a4e65-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)