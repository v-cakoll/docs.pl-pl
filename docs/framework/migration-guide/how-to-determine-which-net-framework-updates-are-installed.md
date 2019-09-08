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
ms.openlocfilehash: c4c505c679c46494f7dc2534c2bbe9f50243a7dd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790067"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Instrukcje: Określanie, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane

W tym artykule opisano, jak dowiedzieć się, które .NET Framework aktualizacje zabezpieczeń i poprawki są zainstalowane na komputerze.

> [!NOTE]
> Wszystkie techniki przedstawione w tym artykule wymagają konta z uprawnieniami administracyjnymi.

## <a name="to-find-installed-updates-using-the-registry"></a>Aby znaleźć zainstalowane aktualizacje przy użyciu rejestru

Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows. Aby wyświetlić te informacje, można użyć programu edytora rejestru (*regedit. exe*).

1. Otwórz program **regedit. exe**. W systemie Windows 8 i nowszych wersjach kliknij prawym przyciskiem myszy pozycję **Uruchom** ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), a następnie wybierz polecenie **Uruchom**. W polu **Otwórz** wprowadź ciąg **regedit** , a następnie wybierz **przycisk OK**.

2. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Zainstalowane aktualizacje są wymienione w obszarze podkluczy, które identyfikują .NET Framework wersji, do których mają zastosowanie. Każda aktualizacja jest identyfikowana przez numer bazy wiedzy (KB).

W Edytorze rejestru wersje .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach. Informacje o wykrywaniu zainstalowanych numerów wersji znajdują się [w temacie How to: Ustal, które wersje .NET Framework są](how-to-determine-which-versions-are-installed.md)zainstalowane.

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

- [Instrukcje: Ustal, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md)
- [Zainstaluj .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Wersje i zależności](versions-and-dependencies.md)
