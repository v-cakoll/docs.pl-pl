---
title: "Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)
To narzędzie wiersza polecenia można pobrać klucza prywatnego z magazynu certyfikatów. FindPrivateKey.exe można na przykład, aby znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów.  
  
> [!IMPORTANT]
>  Narzędzie FindPrivateKey jest dostarczana jako przykład WCF. Aby uzyskać więcej informacji o tym, gdzie można znaleźć próbki i skompiluj go, zobacz  
  
## <a name="syntax"></a>Składnia  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>Uwagi  
 W poniższych tabelach opisano argumenty i opcje, które mogą służyć za pomocą narzędzia Znajdź klucza prywatnego (FindPrivateKey.exe).  
  
|Argument|Opis|  
|--------------|-----------------|  
|`storeName`|Nazwa magazynu certyfikatów.|  
|`storeLocation`|Lokalizacja magazynu certyfikatów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|Określa nazwę podmiotu certyfikatu.|  
|`/t <`*odcisk palca*`>`|Określa odcisk palca certyfikatu. Certmgr.exe umożliwia pobieranie odcisku palca certyfikatu.|  
|`/f`|Wyświetla tylko nazwę pliku.|  
|`/d`|Wyświetla tylko katalog.|  
|`/a`|Generuje bezwzględnej nazwy pliku.|  
  
## <a name="examples"></a>Przykłady  
 Polecenie pobiera klucz prywatny dla Jan Nowak.  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 Polecenie pobiera klucz prywatny dla komputera lokalnego.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
