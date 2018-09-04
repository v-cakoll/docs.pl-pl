---
title: -baseaddress (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 58d1511387c93841f49d6ced934b492fe097876b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518523"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (opcje kompilatora C#)
**- Baseaddress** pozwala określić preferowany adres podstawowy, w którym można załadować biblioteki DLL. Aby uzyskać więcej informacji na temat kiedy i dlaczego użyć tej opcji, zobacz [WebLog Ostermana Larry'ego](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Adres podstawowy DLL. Ten adres można określić jako dziesiętne, liczbę szesnastkową lub ósemkowo.  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez .NET Framework środowisko uruchomieniowe języka wspólnego.  
  
 Należy pamiętać, zostanie zaokrąglony word niższego rzędu w tym adresie. Na przykład jeśli określisz 0x11110001, zostanie on zaokrąglony do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, należy użyć SN. EXE z opcją -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** stronę właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **adres podstawowy DLL** właściwości.  
  
     Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Zobacz też  

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
