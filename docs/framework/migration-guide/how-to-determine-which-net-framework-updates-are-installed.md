---
title: "Porady: Określanie, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane"
description: "Dowiedz się, jak ustalić, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane na komputerze."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Porady: Określanie, które poprawki i aktualizacje zabezpieczeń .NET Framework są zainstalowane

W tym artykule przedstawiono sposób sprawdzić aktualizacje zabezpieczeń .NET Framework i poprawki są instalowane na komputerze.

> [!NOTE]
> Wszystkie techniki, które są wyświetlane w tym artykule wymagają konta z uprawnieniami administracyjnymi.

## <a name="to-find-installed-updates-using-the-registry"></a>Aby znaleźć zainstalowane aktualizacje za pomocą rejestru

Zainstalowane aktualizacje i poprawki dla każdej wersji platformy .NET zainstalowany na komputerze są wyświetlane w rejestrze systemu Windows. Edytor rejestru (*regedit.exe*) program, aby wyświetlić te informacje.

1. Otwórz program **regedit.exe**. W systemie Windows 8 i nowszych wersjach, kliknij prawym przyciskiem myszy **Start** ![logo systemu Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), a następnie wybierz pozycję **Uruchom**. W **Otwórz** wprowadź **regedit** i wybierz **OK**.

2. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Zainstalowane aktualizacje są wyświetlane w obszarze podklucze identyfikowania wersji .NET Framework, które odnoszą się do. Każda aktualizacja jest identyfikowany przez numer bazy wiedzy Knowledge Base (KB).

W Edytorze rejestru wersje programu .NET Framework i zainstalowanych aktualizacji dla każdej wersji, są przechowywane w różnych podkluczy. Uzyskać informacji na temat wykrywania numery zainstalowanej wersji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Aby znaleźć zainstalowane aktualizacje, badając rejestru w kodzie

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Aby znaleźć zainstalowane aktualizacje, badając rejestru w programie PowerShell

Poniższy przykład przedstawia sposób określenia aktualizacje zabezpieczeń .NET Framework i poprawki, które są zainstalowane na komputerze przy użyciu programu PowerShell:

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

Przykład generuje dane wyjściowe podobne do następującego:

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a>Zobacz także

[Porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)  
[Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
