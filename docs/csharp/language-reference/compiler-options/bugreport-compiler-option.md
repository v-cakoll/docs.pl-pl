---
title: -bugreport (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 5505971ad9a6920124dd4d8c12642a5e4e346322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="06dd6-102">-bugreport (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="06dd6-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="06dd6-103">Określa, czy informacje o debugowaniu powinna zostać umieszczona w pliku w celu późniejszej analizy.</span><span class="sxs-lookup"><span data-stu-id="06dd6-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06dd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06dd6-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="06dd6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="06dd6-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="06dd6-106">Nazwa pliku, który ma zawierać raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="06dd6-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06dd6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06dd6-107">Remarks</span></span>  
 <span data-ttu-id="06dd6-108">**- Bugreport** opcja określa, że następujące informacje powinny być umieszczone w `file`:</span><span class="sxs-lookup"><span data-stu-id="06dd6-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
-   <span data-ttu-id="06dd6-109">Kopiowanie wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06dd6-109">A copy of all source code files in the compilation.</span></span>  
  
-   <span data-ttu-id="06dd6-110">Lista opcje kompilatora używane w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06dd6-110">A listing of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="06dd6-111">Informacje o wersji o kompilatora, czas wykonywania i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="06dd6-111">Version information about your compiler, run time, and operating system.</span></span>  
  
-   <span data-ttu-id="06dd6-112">Zestawy występujące w odwołaniach i modułów, zapisany jako cyfr szesnastkowych, z wyjątkiem zestawy, które są dostarczane z programu .NET Framework i zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="06dd6-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
-   <span data-ttu-id="06dd6-113">Kompilator output, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="06dd6-113">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="06dd6-114">Opis problemu, który pojawi się monit o.</span><span class="sxs-lookup"><span data-stu-id="06dd6-114">A description of the problem, which you will be prompted for.</span></span>  
  
-   <span data-ttu-id="06dd6-115">Opis sposobu uważasz, że problem należy ustalić, który pojawi się monit o.</span><span class="sxs-lookup"><span data-stu-id="06dd6-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="06dd6-116">Jeśli ta opcja jest używana z **- errorreport: wiersz** lub **- errorreport: wysyłanie**, informacje w pliku będą wysyłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="06dd6-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="06dd6-117">Ponieważ kopię wszystkich plików kodu źródłowego zostaną umieszczone w `file`, należy odtworzyć kod podejrzanych wada najkrótszy program możliwe.</span><span class="sxs-lookup"><span data-stu-id="06dd6-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="06dd6-118">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="06dd6-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="06dd6-119">Zwróć uwagę, że zawartość wygenerowanego pliku uwidaczniać kodu źródłowego, co może spowodować ujawnienie informacji przypadkowej.</span><span class="sxs-lookup"><span data-stu-id="06dd6-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06dd6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06dd6-120">See Also</span></span>  
 [<span data-ttu-id="06dd6-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="06dd6-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="06dd6-122">-errorreport (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="06dd6-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [<span data-ttu-id="06dd6-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="06dd6-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
