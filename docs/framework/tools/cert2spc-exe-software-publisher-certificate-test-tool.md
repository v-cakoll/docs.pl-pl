---
title: "Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a8363b0ec059c1ae94b7ab53e5c3064a06541f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)
Narzędzie testowe certyfikatów wydawców oprogramowania tworzy certyfikat wydawcy oprogramowania (SPC) z co najmniej jednego certyfikatu X.509. Cert2spc.exe służy tylko do celów testowych. Prawidłowy SPC można uzyskać od urzędu certyfikacji, np. VeriSign lub Thawte. Aby uzyskać więcej informacji na temat tworzenia certyfikatów X.509, zobacz [Makecert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`certN.cer`|Nazwa certyfikatu X.509 do zawarcia w pliku SPC. Można określić wiele nazw i oddzielić je spacjami.|  
|`crlN.crl`|Nazwa listy odwołania certyfikatów X.509 do zawarcia w pliku SPC. Można określić wiele nazw i oddzielić je spacjami.|  
|`outputSPCfile.spc`|Nazwa obiektu PKCS #7, który zawiera certyfikaty X.509.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie tworzy SPC z `myCertificate.cer` i umieszcza je w `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Poniższe polecenie tworzy SPC z `oneCertificate.cer` i `twoCertificate.cer`i umieszcza je w `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
