---
title: -subsystemversion (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802033"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (Opcje kompilatora C#)

Określa minimalną wersję podsystemu, na którym można uruchomić wygenerowany plik wykonywalny, określając w ten sposób wersje systemu Windows, na których można uruchomić plik wykonywalny. Najczęściej ta opcja gwarantuje, że plik wykonywalny może korzystać z określonych funkcji zabezpieczeń, które nie są dostępne w starszych wersjach systemu Windows.

> [!NOTE]
> Aby określić sam podsystem, należy użyć opcji [-target](./target-compiler-option.md) kompilatora.

## <a name="syntax"></a>Składnia

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametry

`major.minor`

Minimalna wymagana wersja podsystemu, wyrażona w notacji kropkowej dla wersji głównych i pomocniczych. Na przykład można określić, że aplikacja nie może działać w systemie operacyjnym starszym niż Windows 7, jeśli ustawisz wartość tej opcji na 6.01, jak opisano w dalszej tabeli w tym temacie. Należy określić wartości `major` dla `minor` i jako liczby całkowite.

Początkowe zera w `minor` wersji nie zmieniają wersji, ale końcowe zera zrobić. Na przykład 6.1 i 6.01 odnoszą się do tej samej wersji, ale 6.10 odnosi się do innej wersji. Zalecamy wyrażenie wersji pomocniczej jako dwucyfrowej, aby uniknąć nieporozumień.

## <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono typowe wersje systemu Windows w podsystemowych.

|Wersja systemu Windows|Wersja podsystemu|
|---------------------|-----------------------|
|Windows 2000|5,00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Wartości domyślne

Wartość domyślna opcji kompilatora **-subsystemversion** zależy od warunków na poniższej liście:

- Wartość domyślna to 6,02, jeśli ustawiona jest dowolna opcja kompilatora na poniższej liście:

  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [-target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platforma:ramię](./platform-compiler-option.md)

- Wartość domyślna to 6,00, jeśli używasz MSBuild, jesteś przeznaczony do .NET Framework 4.5 i nie ustawiono żadnej z opcji kompilatora, które zostały określone wcześniej na tej liście.

- Wartość domyślna to 4,00, jeśli żaden z poprzednich warunków nie jest spełniony.

## <a name="setting-this-option"></a>Ustawienie tej opcji

Aby ustawić opcję **kompilatora -subsystemversion** w programie Visual Studio, należy otworzyć `SubsystemVersion` plik csproj i określić wartość właściwości w pliku MSBuild XML. Nie można ustawić tej opcji w programie Visual Studio IDE. Aby uzyskać więcej informacji, zobacz "Wartości domyślne" wcześniej w tym temacie lub [Wspólne właściwości projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
