---
title: 'Instrukcje: Dodawanie odwołań do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a666c0e079fb30ecdd32aad64f44434d8253acf4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971903"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="9c844-102">Instrukcje: Dodawanie odwołań do bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="9c844-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="9c844-103">Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane podczas dodawania odwołania do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="9c844-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="9c844-104">Jeśli jest dostępny podstawowy zestaw międzyoperacyjny, program Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9c844-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="9c844-105">Aby dodać odwołanie do biblioteki typów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c844-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="9c844-106">Zainstaluj plik DLL COM lub EXE na komputerze, chyba że plik Instalator systemu Windows. exe przeprowadzi instalację.</span><span class="sxs-lookup"><span data-stu-id="9c844-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="9c844-107">Wybierz **projekt**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="9c844-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="9c844-108">W Menedżerze odwołań wybierz **com**.</span><span class="sxs-lookup"><span data-stu-id="9c844-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="9c844-109">Wybierz bibliotekę typów z listy lub Wyszukaj plik. tlb.</span><span class="sxs-lookup"><span data-stu-id="9c844-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="9c844-110">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="9c844-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="9c844-111">W Eksplorator rozwiązań otwórz menu skrótów dla właśnie dodanego odwołania, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c844-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="9c844-112">W oknie **Właściwości** upewnij się, że właściwość **Osadź typy** współdziałania ma **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="9c844-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="9c844-113">Powoduje to, że program Visual Studio osadzi informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c844-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c844-114">Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c844-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="9c844-115">Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="9c844-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="9c844-116">Generowanie zestawu międzyoperacyjnego zgodnie z opisem [w temacie How to: Generuj zestawy międzyoperacyjnych z](how-to-generate-interop-assemblies-from-type-libraries.md)bibliotek typów.</span><span class="sxs-lookup"><span data-stu-id="9c844-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="9c844-117">Do osadzenia informacji o typie dla typów COM w plikach wykonywalnych Użyj opcji kompilatora [/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) z nazwą zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9c844-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c844-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c844-118">See also</span></span>

- [<span data-ttu-id="9c844-119">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="9c844-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="9c844-120">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c844-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="9c844-121">Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c844-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md) 
- [<span data-ttu-id="9c844-122">/Link (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="9c844-122">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="9c844-123">/Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c844-123">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
