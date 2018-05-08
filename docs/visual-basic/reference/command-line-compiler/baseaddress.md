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
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-baseaddress"></a>-baseaddress
Określa domyślny adres podstawowy, podczas tworzenia biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`address`|Wymagana. Adres podstawowy biblioteki dll. Ten adres należy określić jako liczbę szesnastkową.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Należy pamiętać, że word kolejności dolna ten adres jest zaokrąglana. Na przykład jeśli określisz 0x11110001 jest zaokrąglana do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, należy użyć `–R` opcji narzędzia silne nazewnictwo (Sn.exe).  
  
 Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteki DLL.  
  
|Aby ustawić - baseaddress w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole. **Uwaga:** **adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteki DLL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))
