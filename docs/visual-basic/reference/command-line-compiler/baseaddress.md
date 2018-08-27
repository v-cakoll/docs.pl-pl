---
title: -baseaddress —
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930445"
---
# <a name="-baseaddress"></a>-baseaddress —
Określa domyślny adres podstawowy, podczas tworzenia biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`address`|Wymagane. Adres podstawowy DLL. Ten adres należy określić jako liczbę szesnastkową.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Należy pamiętać, że wyraz niższego rzędu ten adres jest zaokrąglana. Na przykład jeśli określisz 0x11110001, jest zaokrąglana do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, użyj `–R` opcji narzędzie silnych nazw (Sn.exe).  
  
 Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteką DLL.  
  
|Aby ustawić - baseaddress — w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole. **Uwaga:** **adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteką DLL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))
