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
ms.openlocfilehash: d241584195da7d6f74b45b191c4f63204c200d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357183"
---
# <a name="-baseaddress"></a>-baseaddress
Określa domyślny adres podstawowy podczas tworzenia biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`address`|Wymagany. Adres podstawowy biblioteki DLL. Ten adres musi być określony jako liczba szesnastkowa.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez .NET Framework.  
  
 Należy pamiętać, że w tym adresie znajduje się wyraz o niższej kolejności. Na przykład, jeśli określisz 0x11110001, zostanie zaokrąglona do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, użyj `–R` opcji narzędzia silnego nazewnictwa (SN. exe).  
  
 Ta opcja jest ignorowana, jeśli obiekt docelowy nie jest biblioteką DLL.  
  
|Aby ustawić-BaseAddress w środowisku IDE programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. kliknij pozycję **Zaawansowane**.<br />4. Zmodyfikuj wartość w polu **adres podstawowy biblioteki dll:** . **Uwaga:**      **Adres podstawowy biblioteki dll:** pole jest tylko do odczytu, chyba że obiekt docelowy jest biblioteką DLL.|  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-Target (Visual Basic)](target.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md))
