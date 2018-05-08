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
ms.openlocfilehash: 3759067731902ba4f460ff850fb5e81f2e544e99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (opcje kompilatora C#)
**- Baseaddress** pozwala określić preferowany adres podstawowy, w którym można załadować biblioteki DLL. Aby uzyskać więcej informacji na temat kiedy i dlaczego użyć tej opcji, zobacz [WebLog Larry Ostermana](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Adres podstawowy biblioteki dll. Ten adres można określić jako liczbę szesnastkową lub ósemkowo dziesiętnych.  
  
## <a name="remarks"></a>Uwagi  
 Domyślny adres podstawowy biblioteki DLL jest ustawiana przez .NET Framework środowisko uruchomieniowe języka wspólnego.  
  
 Należy pamiętać, zostanie zaokrąglony word kolejności dolna ten adres. Na przykład jeśli określisz 0x11110001, zostanie on zaokrąglony do 0x11110000.  
  
 Aby ukończyć proces podpisywania dla biblioteki DLL, użyj SN. EXE z opcją -R.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **adres podstawowy DLL** właściwości.  
  
     Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
