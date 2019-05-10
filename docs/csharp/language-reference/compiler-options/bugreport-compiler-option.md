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
ms.openlocfilehash: f25455fac84903f9c39861e1f6863f6b2f6928f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587392"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="a9ff0-102">-bugreport (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a9ff0-102">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="a9ff0-103">Określa, że informacje o debugowaniu należy umieścić w pliku do późniejszej analizy.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-103">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9ff0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9ff0-104">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="a9ff0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a9ff0-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="a9ff0-106">Nazwa pliku który ma zawierać raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-106">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9ff0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9ff0-107">Remarks</span></span>  
 <span data-ttu-id="a9ff0-108">**- Bugreport** opcja określa, że następujące informacje powinny być umieszczone w `file`:</span><span class="sxs-lookup"><span data-stu-id="a9ff0-108">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="a9ff0-109">Kopiowanie wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-109">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="a9ff0-110">Lista opcji kompilatora, używane w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-110">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="a9ff0-111">Informacje o wersji dotyczące kompilatora, w czasie wykonywania i w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-111">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="a9ff0-112">Zestawy referencyjne i moduły, zapisane jako cyfra szesnastkowa, z wyjątkiem zestawów, które są dostarczane z .NET Framework i zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-112">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="a9ff0-113">Kompilator dane wyjściowe, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-113">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="a9ff0-114">Opis problemu, który zostanie wyświetlony monit dla.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-114">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="a9ff0-115">Opis sposobu Twoim zdaniem ten problem należy ustalić, który zostanie wyświetlony monit dla.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-115">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="a9ff0-116">Jeśli ta opcja jest używana z **- errorreport: wiersz** lub **- errorreport: wysyłanie**, informacje w pliku będą wysyłane do firmy Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-116">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="a9ff0-117">Ponieważ kopię wszystkich plikach kodu źródłowego zostaną umieszczone w `file`, należy odtworzyć kod potencjalnie złośliwych programów wada najkrótszej program możliwe.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-117">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="a9ff0-118">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-118">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="a9ff0-119">Należy zauważyć, że zawartość pliku wygenerowanego udostępnienia kodu źródłowego, co może spowodować ujawnienie informacji przypadkowego.</span><span class="sxs-lookup"><span data-stu-id="a9ff0-119">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ff0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9ff0-120">See also</span></span>

- [<span data-ttu-id="a9ff0-121">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a9ff0-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="a9ff0-122">-errorreport (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a9ff0-122">-errorreport (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)
- [<span data-ttu-id="a9ff0-123">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a9ff0-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
