---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: e8dfe95ef3385635f5839ecc96047911544a256e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591448"
---
# <a name="-baseaddress"></a><span data-ttu-id="cf09c-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="cf09c-102">-baseaddress</span></span>
<span data-ttu-id="cf09c-103">Określa domyślny adres podstawowy, podczas tworzenia biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="cf09c-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf09c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf09c-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf09c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cf09c-105">Arguments</span></span>  
  
|<span data-ttu-id="cf09c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cf09c-106">Term</span></span>|<span data-ttu-id="cf09c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cf09c-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="cf09c-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cf09c-108">Required.</span></span> <span data-ttu-id="cf09c-109">Adres podstawowy DLL.</span><span class="sxs-lookup"><span data-stu-id="cf09c-109">The base address for the DLL.</span></span> <span data-ttu-id="cf09c-110">Ten adres należy określić jako liczbę szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="cf09c-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf09c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf09c-111">Remarks</span></span>  
 <span data-ttu-id="cf09c-112">Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf09c-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="cf09c-113">Należy pamiętać, że wyraz niższego rzędu ten adres jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="cf09c-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="cf09c-114">Na przykład jeśli określisz 0x11110001, jest zaokrąglana do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="cf09c-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="cf09c-115">Aby ukończyć proces podpisywania dla biblioteki DLL, użyj `–R` opcji narzędzie silnych nazw (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="cf09c-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="cf09c-116">Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="cf09c-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="cf09c-117">Aby ustawić - baseaddress — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf09c-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="cf09c-118">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="cf09c-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cf09c-119">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cf09c-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="cf09c-120">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="cf09c-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="cf09c-121">3.  Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="cf09c-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="cf09c-122">4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="cf09c-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="cf09c-123">**Uwaga:**      **Adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="cf09c-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf09c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf09c-124">See also</span></span>

- [<span data-ttu-id="cf09c-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf09c-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cf09c-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf09c-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="cf09c-127">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="cf09c-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="cf09c-128">[SN.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="cf09c-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
