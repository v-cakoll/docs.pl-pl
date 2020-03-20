---
title: Zobacz zainstalowane aktualizacje zabezpieczeń i poprawki programu .NET Framework
description: Dowiedz się, jak ustalić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane na komputerze.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181268"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Jak określić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane

W tym artykule pokazano, jak sprawdzić, które aktualizacje zabezpieczeń i poprawki programu .NET Framework są zainstalowane na komputerze.

> [!NOTE]
> Wszystkie techniki pokazane w tym artykule wymagają konta z uprawnieniami administracyjnymi.

## <a name="use-registry-editor"></a>Korzystanie z Edytora rejestru

Zainstalowane aktualizacje zabezpieczeń i poprawki dla każdej wersji programu .NET Framework zainstalowanej na komputerze są wymienione w rejestrze systemu Windows. Do wyświetlenia tych informacji można użyć programu Registry Editor (*regedit.exe).*

1. Otwórz program **regedit.exe**. W systemie Windows 8 i nowszych wersjach kliknij prawym **Run**przyciskiem myszy pozycję ![Rozpocznij zrzut ekranu z logo klucza systemu Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo (dziennik klawiatury systemu Windows)") **Start** W polu **Otwórz** wprowadź **regedit** i wybierz **PRZYCISK OK**.

2. W Edytorze rejestru otwórz następujący podklucz:

     **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**

     Zainstalowane aktualizacje są wyświetlane w podkluczach, które identyfikują wersję programu .NET Framework, do których się odnoszą. Każda aktualizacja jest identyfikowana za pomocą numeru bazy wiedzy (KB).

W Edytorze rejestru wersje programu .NET Framework i zainstalowane aktualizacje dla każdej wersji są przechowywane w różnych podkluczach. Aby uzyskać informacje dotyczące wykrywania zainstalowanych numerów wersji, zobacz [Jak: Określanie zainstalowanych wersji programu .NET Framework](how-to-determine-which-versions-are-installed.md).

## <a name="query-the-registry-using-code"></a>Kwerenda rejestru przy użyciu kodu

Poniższy przykład programowo określa aktualizacje zabezpieczeń programu .NET Framework i poprawki zainstalowane na komputerze:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

W przykładzie daje dane wyjściowe, które są podobne do następującego:

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

## <a name="use-powershell-to-query-the-registry"></a>Używanie programu PowerShell do wykonywania zapytań do rejestru

W poniższym przykładzie pokazano, jak określić aktualizacje zabezpieczeń programu .NET Framework i poprawki zainstalowane na komputerze przy użyciu programu PowerShell:

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

W przykładzie daje dane wyjściowe, które są podobne do następującego:

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

## <a name="see-also"></a>Zobacz też

- [Jak: Określ, które wersje programu .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md)
- [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Wersje i zależności](versions-and-dependencies.md)
