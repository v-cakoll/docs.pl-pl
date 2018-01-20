---
title: Opcje kompilatora C#
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59000f60acdc8ada11bc5abb9e91b5f53d42b9ae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="c-compiler-options"></a><span data-ttu-id="fa378-102">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="fa378-102">C# Compiler Options</span></span>
<span data-ttu-id="fa378-103">Kompilator generuje pliki wykonywalne (.exe), bibliotek dołączanych dynamicznie (dll) lub moduły kodu (modułu .netmodule).</span><span class="sxs-lookup"><span data-stu-id="fa378-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="fa378-104">Każdy — opcja kompilatora jest dostępny w dwóch formach: **-opcja** i **/opcja**.</span><span class="sxs-lookup"><span data-stu-id="fa378-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="fa378-105">Dokumentacja tylko wskazuje **-opcja** formularza.</span><span class="sxs-lookup"><span data-stu-id="fa378-105">The documentation only shows the **-option** form.</span></span>  
  
 <span data-ttu-id="fa378-106">W programie Visual Studio możesz ustawić opcje kompilatora w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="fa378-106">In Visual Studio, you set compiler options in the web.config file.</span></span> <span data-ttu-id="fa378-107">Aby uzyskać więcej informacji, zobacz [ \<kompilatora > elementu](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="fa378-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa378-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fa378-108">In This Section</span></span>  
 [<span data-ttu-id="fa378-109">Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="fa378-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="fa378-110">Informacje dotyczące tworzenia aplikacji programu Visual C# z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa378-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="fa378-111">Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa378-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="fa378-112">Instrukcje dotyczące uruchamiania vsvars32.bat, aby włączyć kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa378-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="fa378-113">Opcje kompilatora C# w rozbiciu na kategorie</span><span class="sxs-lookup"><span data-stu-id="fa378-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="fa378-114">Podzielone na kategorie lista opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fa378-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="fa378-115">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="fa378-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="fa378-116">Alfabetyczną listę opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fa378-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa378-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fa378-117">Related Sections</span></span>  
 [<span data-ttu-id="fa378-118">Tworzenie strony, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="fa378-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="fa378-119">Ustawienie właściwości, które kontrolują sposób kompilowania projektu wbudowanych i debugowania.</span><span class="sxs-lookup"><span data-stu-id="fa378-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="fa378-120">Zawiera informacje na temat niestandardowe kroki procesu kompilacji w projektach Visual C#.</span><span class="sxs-lookup"><span data-stu-id="fa378-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="fa378-121">Domyślnej i niestandardowej kompilacji</span><span class="sxs-lookup"><span data-stu-id="fa378-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="fa378-122">Informacje o typach kompilacji i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa378-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="fa378-123">Przygotowywanie i Zarządzanie kompilacjami</span><span class="sxs-lookup"><span data-stu-id="fa378-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="fa378-124">Procedury tworzenia w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fa378-124">Procedures for building within the Visual Studio development environment.</span></span>
