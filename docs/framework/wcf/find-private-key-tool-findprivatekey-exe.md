---
title: Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 00ad27d28ee3a589d5ee8702bd036b05d8ceb4b3
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637570"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)

To narzędzie wiersza polecenia może służyć do pobierania klucza prywatnego z magazynu certyfikatów. Na przykład *FindPrivateKey.exe* można znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonych w magazynie certyfikatów.

> [!IMPORTANT]
> Narzędzie FindPrivateKey jest dostarczany jako przykładowej usługi WCF. Aby uzyskać więcej informacji na temat miejsca znaleźć plik i jak ją skompilować, zobacz [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Składnia

```
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Uwagi

W poniższych tabelach opisano argumentów i opcje, które mogą służyć za pomocą narzędzia Znajdź klucza prywatnego (FindPrivateKey.exe).

|Argument|Opis|
|--------------|-----------------|
|`storeName`|Nazwa magazynu certyfikatów.|
|`storeLocation`|Lokalizacja magazynu certyfikatów.|

|Opcja|Opis|
|------------|-----------------|
|`/n <` *SubjectName* `>`|Określa nazwę podmiotu certyfikatu.|
|`/t <` *Odcisk palca* `>`|Określa odcisk palca certyfikatu. Certmgr.exe umożliwia pobieranie odcisku palca certyfikatu.|
|`/f`|Wyświetla tylko nazwę pliku.|
|`/d`|Wyświetla tylko katalog.|
|`/a`|Generuje bezwzględnej nazwy pliku.|

## <a name="examples"></a>Przykłady

Następujące polecenie pobiera klucz prywatny dla John Doe:

```
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Następujące polecenie umożliwia pobranie klucza prywatnego na komputerze lokalnym:

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
