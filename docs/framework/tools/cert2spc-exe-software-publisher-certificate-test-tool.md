---
title: Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: 809b7d0383f172a5fbcb2ac4ac3ffb96ff0b8e20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129887"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)
Narzędzie testowe certyfikatów wydawców oprogramowania tworzy certyfikat wydawcy oprogramowania (SPC) z co najmniej jednego certyfikatu X.509. Cert2spc.exe służy tylko do celów testowych. Prawidłowy SPC można uzyskać od urzędu certyfikacji, np. VeriSign lub Thawte. Aby uzyskać więcej informacji na temat tworzenia certyfikatów X.509, zobacz [Makecert.exe (Narzędzie do tworzenia certyfikatów).](/windows/desktop/SecCrypto/makecert)  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|`certN.cer`|Nazwa certyfikatu X.509 do zawarcia w pliku SPC. Można określić wiele nazw i oddzielić je spacjami.|  
|`crlN.crl`|Nazwa listy odwołania certyfikatów X.509 do zawarcia w pliku SPC. Można określić wiele nazw i oddzielić je spacjami.|  
|`outputSPCfile.spc`|Nazwa obiektu PKCS #7, który zawiera certyfikaty X.509.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy chPL `myCertificate.cer` i `mySPCFile.spc`umieszcza go w pliku .  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Następujące polecenie tworzy chPL z `oneCertificate.cer` i `twoCertificate.cer` `mySPCFile.spc`, i umieszcza go w .  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Plik Makecert.exe (narzędzie do tworzenia certyfikatów)](/windows/desktop/SecCrypto/makecert)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
