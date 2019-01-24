---
title: -pdb (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: b0a566931ac76a3adb191f423a497bc446e280c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575505"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="02787-102">-pdb (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="02787-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="02787-103">**- Pdb** — opcja kompilatora Określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="02787-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02787-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02787-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="02787-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="02787-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="02787-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="02787-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02787-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02787-107">Remarks</span></span>  
 <span data-ttu-id="02787-108">Po określeniu [-debug (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilator utworzy plik .pdb w tym samym katalogu, gdzie kompilator utworzy plik wyjściowy (.exe lub .dll) przy użyciu nazwy pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="02787-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="02787-109">**-pdb** służy do określania plików innych niż domyślne nazwę i lokalizację pliku .pdb.</span><span class="sxs-lookup"><span data-stu-id="02787-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="02787-110">Nie można ustawić tę opcję kompilatora w środowisku programowania Visual Studio i nie można go zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="02787-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02787-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="02787-111">Example</span></span>  
 <span data-ttu-id="02787-112">Skompilować `t.cs` i tworzenie pliku .pdb o nazwie tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="02787-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="02787-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02787-113">See also</span></span>

- [<span data-ttu-id="02787-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="02787-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="02787-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="02787-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
