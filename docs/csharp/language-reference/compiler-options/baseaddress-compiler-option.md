---
title: -baseaddress (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cd3269754f783ab8b26683f5215aa81825673e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (opcje kompilatora C#)
**/BaseAddress** pozwala określić preferowany adres podstawowy, w którym można załadować biblioteki DLL. Aby uzyskać więcej informacji na temat kiedy i dlaczego użyć tej opcji, zobacz [WebLog Larry Ostermana](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## <a name="syntax"></a>Składnia  
  
```console  
/baseaddress:address  
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
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
