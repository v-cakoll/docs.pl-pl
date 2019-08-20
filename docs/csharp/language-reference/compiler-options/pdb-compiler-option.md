---
title: -PDB (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602576"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="50d51-102">-PDB (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="50d51-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="50d51-103">**-PDB —** opcja kompilatora określa nazwę i lokalizację pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="50d51-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50d51-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="50d51-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="50d51-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="50d51-106">Nazwa i lokalizacja pliku symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="50d51-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50d51-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50d51-107">Remarks</span></span>  
 <span data-ttu-id="50d51-108">Gdy określisz polecenie [-DebugC# (opcje kompilatora)](./debug-compiler-option.md), kompilator utworzy plik. pdb w tym samym katalogu, w którym kompilator utworzy plik wyjściowy (. exe lub. dll) z nazwą pliku, która jest taka sama jak nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="50d51-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="50d51-109">**-PDB** umożliwia określenie niedomyślnej nazwy pliku i lokalizacji dla pliku. pdb.</span><span class="sxs-lookup"><span data-stu-id="50d51-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="50d51-110">Nie można ustawić tej opcji kompilatora w środowisku deweloperskim programu Visual Studio, ani programowo zmienić.</span><span class="sxs-lookup"><span data-stu-id="50d51-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d51-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="50d51-111">Example</span></span>  
 <span data-ttu-id="50d51-112">Kompiluj `t.cs` i Utwórz plik. pdb o nazwie TT. pdb:</span><span class="sxs-lookup"><span data-stu-id="50d51-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="50d51-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50d51-113">See also</span></span>

- [<span data-ttu-id="50d51-114">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="50d51-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="50d51-115">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="50d51-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
