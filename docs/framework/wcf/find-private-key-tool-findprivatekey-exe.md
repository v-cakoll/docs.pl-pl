---
title: Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990350"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Narzędzie do znajdowania klucza prywatnego (FindPrivateKey.exe)

Za pomocą tego narzędzia wiersza polecenia można pobrać klucz prywatny z magazynu certyfikatów. Na przykład można użyć *FindPrivateKey. exe* , aby znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z konkretnym certyfikatem X. 509 w magazynie certyfikatów.

> [!IMPORTANT]
> Narzędzie FindPrivateKey jest dostarczane jako przykład WCF. Aby uzyskać więcej informacji na temat miejsca znalezienia przykładu i sposobu jego kompilowania, zobacz [FindPrivateKey](./samples/findprivatekey.md).

## <a name="syntax"></a>Składnia

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a>Uwagi

W poniższych tabelach opisano argumenty i opcje, które mogą być używane z narzędziem Znajdź klucz prywatny (FindPrivateKey. exe).

|Argument|Opis|
|--------------|-----------------|
|`storeName`|Nazwa magazynu certyfikatów.|
|`storeLocation`|Lokalizacja magazynu certyfikatów.|

|Opcja|Opis|
|------------|-----------------|
|`/n <`Nr *podmiotu*`>`|Określa nazwę podmiotu certyfikatu.|
|`/t <`*odcisk palca*`>`|Określa odcisk palca certyfikatu. Użyj certmgr. exe w celu pobrania odcisku palca certyfikatu.|
|`/f`|Wyświetla tylko nazwę pliku.|
|`/d`|Wyświetla tylko katalog.|
|`/a`|Wyprowadza bezwzględną nazwę pliku.|

## <a name="examples"></a>Przykłady

Następujące polecenie pobiera klucz prywatny dla John Nowak:

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

Następujące polecenie pobiera klucz prywatny komputera lokalnego:

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
