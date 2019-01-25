---
title: 'Instrukcje: Określanie, które poprawek i aktualizacji zabezpieczeń .NET Framework są zainstalowane'
description: Dowiedz się, jak ustalić, które poprawek i aktualizacji zabezpieczeń .NET Framework są zainstalowane na komputerze.
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
ms.openlocfilehash: e11b2588471e95b4e47fd0efaf41757430b9bb39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604188"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Instrukcje: Określanie, które poprawek i aktualizacji zabezpieczeń .NET Framework są zainstalowane

W tym artykule dowiesz się, jak sprawdzić aktualizacje zabezpieczeń .NET Framework i poprawki są zainstalowane na komputerze.

> [!NOTE]
> Wszystkie techniki przedstawione w tym artykule wymaga konta z uprawnieniami administracyjnymi.

## <a name="to-find-installed-updates-using-the-registry"></a>Aby znaleźć zainstalowane aktualizacje, za pomocą rejestru

Zainstalowane aktualizacje i poprawki dla każdej wersji programu .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows. Edytor rejestru (*regedit.exe*) program, aby wyświetlić te informacje.

1. Otwórz program **regedit.exe**. W systemie Windows 8 i nowszych wersjach, kliknij prawym przyciskiem myszy **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), a następnie wybierz **Uruchom**. W **Otwórz** wprowadź **regedit** i wybierz **OK**.

2. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Zainstalowane aktualizacje są wymienione w podkluczy, które identyfikują wersja programu .NET Framework, które odnoszą się do. Każda aktualizacja jest identyfikowany przez numer bazy wiedzy Knowledge Base (KB).

W Edytorze rejestru wersje programu .NET Framework i zainstalowanych aktualizacji dla każdej wersji, są przechowywane w różnych podkluczy. Aby dowiedzieć się, jak wykrywanie numery zainstalowanej wersji, zobacz [jak: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Aby znaleźć zainstalowane aktualizacje, wykonując zapytanie w rejestrze w kodzie

Poniższy przykład określa programowo, aktualizacje zabezpieczeń .NET Framework i poprawki, które są zainstalowane na komputerze:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Aby znaleźć zainstalowane aktualizacje, wykonując zapytanie w rejestrze w programie PowerShell

Poniższy przykład pokazuje, jak określić aktualizacje zabezpieczeń .NET Framework i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:

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

- [Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)
- [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)
- [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
