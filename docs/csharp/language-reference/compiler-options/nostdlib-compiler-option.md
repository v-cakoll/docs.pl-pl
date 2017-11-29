---
title: -nostdlib (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad3ca7775512623de43c7fe6b7fe1cf481ccca87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="nostdlib-c-compiler-options"></a><span data-ttu-id="d39c5-102">/nostdlib (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d39c5-102">/nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="d39c5-103">**/ nostdlib** uniemożliwia importowanie pliku mscorlib.dll, która określa całą przestrzeń nazw systemu.</span><span class="sxs-lookup"><span data-stu-id="d39c5-103">**/nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d39c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d39c5-104">Syntax</span></span>  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d39c5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d39c5-105">Remarks</span></span>  
 <span data-ttu-id="d39c5-106">Użyj tej opcji, jeśli chcesz zdefiniować lub utworzyć własne systemową przestrzenią nazw i obiektów.</span><span class="sxs-lookup"><span data-stu-id="d39c5-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="d39c5-107">Jeśli nie określisz **/nostdlib**, mscorlib.dll zostaną zaimportowane do programu (jak w przypadku określania **/nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="d39c5-107">If you do not specify **/nostdlib**, mscorlib.dll will be imported into your program (same as specifying **/nostdlib-**).</span></span> <span data-ttu-id="d39c5-108">Określanie **/nostdlib** jest taka sama jak określanie **/nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="d39c5-108">Specifying **/nostdlib** is the same as specifying **/nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d39c5-109">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d39c5-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d39c5-110">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="d39c5-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="d39c5-111">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d39c5-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="d39c5-112">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d39c5-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="d39c5-113">Modyfikowanie **nie odwołuj się do pliku mscorlib.dll** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d39c5-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="d39c5-114">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="d39c5-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39c5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d39c5-115">See Also</span></span>  
 [<span data-ttu-id="d39c5-116">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d39c5-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
