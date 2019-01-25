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
ms.openlocfilehash: 0fecc8e890f44512fe4ac2058f26fe54db7570a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588616"
---
# <a name="-baseaddress"></a><span data-ttu-id="88c7a-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="88c7a-102">-baseaddress</span></span>
<span data-ttu-id="88c7a-103">Określa domyślny adres podstawowy, podczas tworzenia biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="88c7a-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88c7a-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="88c7a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="88c7a-105">Arguments</span></span>  
  
|<span data-ttu-id="88c7a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="88c7a-106">Term</span></span>|<span data-ttu-id="88c7a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="88c7a-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="88c7a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="88c7a-108">Required.</span></span> <span data-ttu-id="88c7a-109">Adres podstawowy DLL.</span><span class="sxs-lookup"><span data-stu-id="88c7a-109">The base address for the DLL.</span></span> <span data-ttu-id="88c7a-110">Ten adres należy określić jako liczbę szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="88c7a-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88c7a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88c7a-111">Remarks</span></span>  
 <span data-ttu-id="88c7a-112">Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88c7a-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="88c7a-113">Należy pamiętać, że wyraz niższego rzędu ten adres jest zaokrąglana.</span><span class="sxs-lookup"><span data-stu-id="88c7a-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="88c7a-114">Na przykład jeśli określisz 0x11110001, jest zaokrąglana do 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="88c7a-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="88c7a-115">Aby ukończyć proces podpisywania dla biblioteki DLL, użyj `–R` opcji narzędzie silnych nazw (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="88c7a-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="88c7a-116">Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="88c7a-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="88c7a-117">Aby ustawić - baseaddress — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88c7a-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="88c7a-118">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="88c7a-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="88c7a-119">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="88c7a-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="88c7a-120">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="88c7a-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="88c7a-121">3.  Kliknij przycisk **zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="88c7a-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="88c7a-122">4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole.</span><span class="sxs-lookup"><span data-stu-id="88c7a-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="88c7a-123">**Uwaga:**      **Adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="88c7a-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88c7a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88c7a-124">See also</span></span>
- [<span data-ttu-id="88c7a-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88c7a-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="88c7a-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88c7a-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="88c7a-127">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="88c7a-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="88c7a-128">[Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="88c7a-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
