---
title: 'Instrukcje: Określanie, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane'
description: Dowiedz się, jak określić, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c69d4bb370087dddafbfed41cbfb1fef229677c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318972"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Instrukcje: Określanie, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane

W tym artykule opisano, jak dowiedzieć się, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.

> [!NOTE]
> Wszystkie techniki przedstawione w tym artykule wymagają konta z uprawnieniami administracyjnymi.

## <a name="to-find-installed-updates-using-the-registry"></a>Aby znaleźć zainstalowane aktualizacje przy użyciu rejestru

Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows. Aby wyświetlić te informacje, można użyć programu edytora rejestru (*regedit. exe*).

1. Otwórz program **regedit. exe**. W systemie Windows 8 i nowszych wersjach kliknij prawym przyciskiem myszy **Start** ![zrzut ekranu logo klucza systemu Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), a następnie wybierz pozycję **Uruchom**. W polu **Otwórz** wprowadź ciąg **regedit** , a następnie wybierz **przycisk OK**.

2. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Zainstalowane aktualizacje są wymienione w obszarze podkluczy, które identyfikują .NET Framework wersji, do których mają zastosowanie. Każda aktualizacja jest identyfikowana przez numer bazy wiedzy (KB).

W Edytorze rejestru wersje .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach. Informacje o wykrywaniu zainstalowanych numerów wersji znajdują się w temacie [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Aby znaleźć zainstalowane aktualizacje, badając rejestr w kodzie

Poniższy przykład programowo określa .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Przykład generuje dane wyjściowe podobne do następującego:

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Aby znaleźć zainstalowane aktualizacje, badając rejestr w programie PowerShell

Poniższy przykład pokazuje, jak określić .NET Framework aktualizacje zabezpieczeń i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

Przykład generuje dane wyjściowe podobne do następującego:

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md)
- [Zainstaluj .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Wersje i zależności](versions-and-dependencies.md)
