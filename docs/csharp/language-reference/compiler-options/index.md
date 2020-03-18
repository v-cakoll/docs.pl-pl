---
title: Opcje kompilatora C#
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: 787f9c5fff79eb67e2d74043782532c1fc4034b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972747"
---
# <a name="c-compiler-options"></a><span data-ttu-id="23d9a-102">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="23d9a-102">C# Compiler Options</span></span>

<span data-ttu-id="23d9a-103">Kompilator tworzy pliki wykonywalne (exe), biblioteki łączy dynamicznych (dll) lub moduły kodu (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="23d9a-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="23d9a-104">Każda opcja kompilatora jest dostępna w dwóch formach: **-option** i **/option**.</span><span class="sxs-lookup"><span data-stu-id="23d9a-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="23d9a-105">W dokumentacji jest wyświetlany tylko formularz **opcji.**</span><span class="sxs-lookup"><span data-stu-id="23d9a-105">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="23d9a-106">W programie Visual Studio można ustawić opcje kompilatora w pliku *web.config.*</span><span class="sxs-lookup"><span data-stu-id="23d9a-106">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="23d9a-107">Aby uzyskać więcej informacji, zobacz [ \<kompilator> element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="23d9a-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="23d9a-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23d9a-108">In this section</span></span>

- <span data-ttu-id="23d9a-109">[Tworzenie wiersza polecenia z csc.exe](command-line-building-with-csc-exe.md) Informacje o tworzeniu aplikacji Visual C# z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="23d9a-109">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="23d9a-110">[Jak ustawić zmienne środowiskowe dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Zawiera kroki uruchamiania *vsvars32.bat,* aby włączyć kompilacje wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="23d9a-110">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="23d9a-111">[Opcje kompilatora Języka C# wymienione według kategorii](listed-by-category.md) Kategoryczna lista opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23d9a-111">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="23d9a-112">[Opcje kompilatora Języka C# wymienione alfabetycznie](listed-alphabetically.md) Alfabetyczna lista opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23d9a-112">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="23d9a-113">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="23d9a-113">Related sections</span></span>

- <span data-ttu-id="23d9a-114">[Strona kompilacji, Projektant projektu](/visualstudio/ide/reference/build-page-project-designer-csharp) Ustawianie właściwości, które regulują sposób projektu jest kompilowany, zbudowany i debugowane.</span><span class="sxs-lookup"><span data-stu-id="23d9a-114">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="23d9a-115">Zawiera informacje o krokach kompilacji niestandardowej w projektach visual c#.</span><span class="sxs-lookup"><span data-stu-id="23d9a-115">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="23d9a-116">[Kompilacje domyślne i niestandardowe](/visualstudio/ide/compiling-and-building-in-visual-studio) Informacje o typach kompilacji i konfiguracjach.</span><span class="sxs-lookup"><span data-stu-id="23d9a-116">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="23d9a-117">[Przygotowywanie kompilacji i zarządzanie nimi](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedury tworzenia w środowisku programistycznym Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23d9a-117">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
