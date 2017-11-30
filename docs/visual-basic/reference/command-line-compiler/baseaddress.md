---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be88bf4834ca58b1fe708eb1ef7188c583fef0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress"></a>/baseaddress
Określa domyślny adres podstawowy, podczas tworzenia biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`address`|Wymagany. Adres podstawowy biblioteki dll. Ten adres należy określić jako liczbę szesnastkową.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Należy pamiętać, że word kolejności dolna ten adres jest zaokrąglana. Na przykład jeśli określisz 0x11110001 jest zaokrąglana do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, należy użyć `–R` opcji narzędzia silne nazewnictwo (Sn.exe).  
  
 Ta opcja jest ignorowana, jeśli element docelowy nie jest biblioteki DLL.  
  
|Aby ustawić/baseAddress w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane**.<br />4.  Zmodyfikuj wartość w **adres podstawowy DLL:** pole. **Uwaga:** **adres podstawowy DLL:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteki DLL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [SN.exe (narzędzie silnych nazw)](https://msdn.microsoft.com/library/k5b5tt23)
