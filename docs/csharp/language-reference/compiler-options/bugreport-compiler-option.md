---
title: -bugreport (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603079"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="03cd6-102">-bugreport (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="03cd6-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="03cd6-103">Określa, że informacje debugowania powinny być umieszczane w pliku do późniejszej analizy.</span><span class="sxs-lookup"><span data-stu-id="03cd6-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03cd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03cd6-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="03cd6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="03cd6-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="03cd6-106">Nazwa pliku, który ma zawierać raport o błędzie.</span><span class="sxs-lookup"><span data-stu-id="03cd6-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03cd6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03cd6-107">Remarks</span></span>  
 <span data-ttu-id="03cd6-108">Opcja **-bugreport** określa, że następujące informacje `file`powinny być umieszczone w:</span><span class="sxs-lookup"><span data-stu-id="03cd6-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="03cd6-109">Kopia wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="03cd6-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="03cd6-110">Lista opcji kompilatora używanych w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="03cd6-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="03cd6-111">Informacje o wersji kompilatora, czasu wykonywania i systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="03cd6-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="03cd6-112">Odwołuje się do zestawów i modułów, zapisane jako cyfry szesnastkowe, z wyjątkiem zestawów, które są dostarczany z .NET Framework i SDK.</span><span class="sxs-lookup"><span data-stu-id="03cd6-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="03cd6-113">Dane wyjściowe kompilatora, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="03cd6-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="03cd6-114">Opis problemu, do którego zostaniesz poproszony.</span><span class="sxs-lookup"><span data-stu-id="03cd6-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="03cd6-115">Opis tego, jak twoim zdaniem problem powinien zostać rozwiązany, o który zostaniesz poproszony.</span><span class="sxs-lookup"><span data-stu-id="03cd6-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="03cd6-116">Jeśli ta opcja jest używana z **-errorreport:prompt** lub **-errorreport:send,** informacje w pliku zostaną wysłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="03cd6-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="03cd6-117">Ponieważ kopia wszystkich plików kodu źródłowego `file`zostanie umieszczona w , można odtworzyć podejrzewaną wadę kodu w jak najkrótszym programie.</span><span class="sxs-lookup"><span data-stu-id="03cd6-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="03cd6-118">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="03cd6-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="03cd6-119">Należy zauważyć, że zawartość wygenerowanego pliku uwidacznia ją kodem źródłowym, co może spowodować nieumyślne ujawnienie informacji.</span><span class="sxs-lookup"><span data-stu-id="03cd6-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03cd6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03cd6-120">See also</span></span>

- [<span data-ttu-id="03cd6-121">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="03cd6-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="03cd6-122">-errorreport (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="03cd6-122">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="03cd6-123">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="03cd6-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
