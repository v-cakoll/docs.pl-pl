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
ms.openlocfilehash: 733013c8eca75bad0dc0bdf1d76f1468b1d903a8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759395"
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
|`address`|Wymagana. Adres podstawowy DLL. Ten adres należy określić jako liczbę szesnastkową.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Należy pamiętać, że wyraz niższego rzędu ten adres jest zaokrąglana. Na przykład jeśli określisz 0x11110001, jest zaokrąglana do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, użyj `–R` opcji narzędzie silnych nazw (Sn.exe).  
  
 Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteką DLL.  
  
|Aby ustawić - baseaddress — w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole. **Uwaga:**      **Adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteką DLL.|  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [SN.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))
