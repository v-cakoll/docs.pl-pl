---
title: -bugreport (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603079"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="6471e-102">-bugreport (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="6471e-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="6471e-103">Określa, że informacje debugowania należy umieścić w pliku do późniejszej analizy.</span><span class="sxs-lookup"><span data-stu-id="6471e-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6471e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6471e-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="6471e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6471e-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="6471e-106">Nazwa pliku, który ma zawierać raport o błędach.</span><span class="sxs-lookup"><span data-stu-id="6471e-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6471e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6471e-107">Remarks</span></span>  
 <span data-ttu-id="6471e-108">Opcja **-bugreport** określa, że należy umieścić `file`następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="6471e-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="6471e-109">Kopia wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6471e-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="6471e-110">Lista opcji kompilatora używanych w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6471e-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="6471e-111">Informacje o wersji dotyczące kompilatora, czasu wykonywania i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6471e-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="6471e-112">Przywoływane zestawy i moduły, zapisane w postaci cyfr szesnastkowych, z wyjątkiem zestawów, które są dostarczane z .NET Framework i zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="6471e-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="6471e-113">Dane wyjściowe kompilatora, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="6471e-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="6471e-114">Opis problemu, dla którego zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="6471e-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="6471e-115">Opis sposobu, w jaki sądzisz, że problem powinien zostać naprawiony, zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="6471e-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="6471e-116">Jeśli ta opcja jest używana z poleceniem **-errorReport: Prompt** lub **-errorReport: Send**, informacje w pliku będą wysyłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="6471e-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="6471e-117">Ze względu na to, że kopia wszystkich plików kodu źródłowego `file`zostanie umieszczona w programie, może być konieczne odtworzenie podejrzanej wady kodu w najkrótszym możliwym programie.</span><span class="sxs-lookup"><span data-stu-id="6471e-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="6471e-118">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="6471e-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="6471e-119">Zauważ, że zawartość wygenerowanego pliku uwidacznia kod źródłowy, który może spowodować nieumyślne ujawnienie informacji.</span><span class="sxs-lookup"><span data-stu-id="6471e-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6471e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6471e-120">See also</span></span>

- [<span data-ttu-id="6471e-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="6471e-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6471e-122">-errorreport (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="6471e-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="6471e-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6471e-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
