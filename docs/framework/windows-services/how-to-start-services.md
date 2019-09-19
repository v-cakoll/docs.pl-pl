---
title: 'Instrukcje: Uruchamianie usług'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 75fd3aba88bdffbe536ad5dab14996913d0a9d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053574"
---
# <a name="how-to-start-services"></a>Instrukcje: Uruchamianie usług

Po zainstalowaniu usługi należy ją uruchomić. Rozpoczęcie wywołuje <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę w klasie usługi. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Zwykle Metoda definiuje przydatną służbę wykonywaną przez usługę. Po uruchomieniu usługa pozostaje aktywna, dopóki nie zostanie ręcznie wstrzymana lub zatrzymana.

Usługi można skonfigurować do automatycznego uruchamiania lub ręcznie. Usługa uruchamiana automatycznie zostanie uruchomiona, gdy komputer, na którym jest zainstalowany, jest ponownie uruchamiana lub włączona. Użytkownik musi uruchomić usługę, która jest uruchamiana ręcznie.

> [!NOTE]
> Domyślnie usługi utworzone za pomocą programu Visual Studio są ustawiane jako uruchamiane ręcznie.

Istnieje kilka sposobów, aby ręcznie uruchomić usługę — od **Eksplorator serwera**, z **Menedżera sterowania usługami**lub z kodu przy użyciu <xref:System.ServiceProcess.ServiceController>składnika o nazwie.

Należy ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość w klasie, <xref:System.ServiceProcess.ServiceInstaller> aby określić, czy usługa powinna być uruchamiana ręcznie czy automatycznie.

### <a name="to-specify-how-a-service-should-start"></a>Aby określić sposób uruchamiania usługi

1. Po utworzeniu usługi należy dodać do niej niezbędne Instalatory. Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](how-to-add-installers-to-your-service-application.md)usługi.

2. W projektancie kliknij Instalatora usługi dla usługi, z którą pracujesz.

3. W oknie **Właściwości** Ustaw <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość na jedną z następujących opcji:

    |Aby zainstalować usługę|Ustaw tę wartość|
    |----------------------------------|--------------------|
    |Po ponownym uruchomieniu komputera|**Automatyczne**|
    |Po uruchomieniu przez jawną akcję użytkownika|**Ręcznie**|

    > [!TIP]
    > Aby zapobiec uruchamianiu usługi w ogóle, można ustawić <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> właściwość na wartość **wyłączone**. Można to zrobić, jeśli zamierzasz ponownie uruchomić serwer kilka razy i chcesz zaoszczędzić czas, zapobiegając usługom, które normalnie zaczynają się od uruchamiania.

    > [!NOTE]
    > Te i inne właściwości można zmienić po zainstalowaniu usługi.

    Istnieje kilka sposobów, w których można uruchomić usługę, która ma <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> swój proces ustawiony na **ręczny** — od **Eksplorator serwera**, z **Menedżera sterowania usługami systemu Windows**lub z kodu. Należy pamiętać, że nie wszystkie te metody faktycznie uruchamiają usługę w kontekście **Menedżera kontroli usług**. **Eksplorator serwera** i programowe metody uruchamiania usługi faktycznie manipulują kontrolerem.

### <a name="to-manually-start-a-service-from-server-explorer"></a>Aby ręcznie uruchomić usługę z Eksplorator serwera

1. W **Eksplorator serwera**Dodaj serwer, którego chcesz użyć, jeśli nie jest jeszcze wymieniony. Aby uzyskać więcej informacji, zobacz How to: Dostęp i Inicjowanie Eksplorator serwera-Eksplorator bazy danych.

2. Rozwiń węzeł **usługi** , a następnie Znajdź usługę, którą chcesz uruchomić.

3. Kliknij prawym przyciskiem myszy nazwę usługi, a następnie kliknij przycisk **Uruchom**.

### <a name="to-manually-start-a-service-from-services-control-manager"></a>Aby ręcznie uruchomić usługę za pomocą Menedżera kontroli usług

1. Otwórz **Menedżera kontroli usług** , wykonując jedną z następujących czynności:

    - W systemach Windows XP i 2000 Professional kliknij prawym przyciskiem myszy ikonę **mój komputer** na pulpicie, a następnie kliknij polecenie **Zarządzaj**. W wyświetlonym oknie dialogowym Rozwiń węzeł **usługi i aplikacje** .

      \- lub —

    - W systemie Windows Server 2003 i Windows 2000 Server, kliknij przycisk **Start**, wskaż polecenie **programy**, kliknij polecenie **Narzędzia administracyjne**, a następnie kliknij pozycję **usługi**.

      > [!NOTE]
      > W systemie Windows NT w wersji 4,0 można otworzyć to okno dialogowe z **Panelu sterowania**.

    Twoja usługa powinna zostać wyświetlona w sekcji **usługi** okna.

2. Wybierz usługę na liście, kliknij ją prawym przyciskiem myszy, a następnie kliknij przycisk **Uruchom**.

### <a name="to-manually-start-a-service-from-code"></a>Aby ręcznie uruchomić usługę z kodu

1. Utwórz wystąpienie <xref:System.ServiceProcess.ServiceController> klasy i skonfiguruj je do współpracy z usługą, którą chcesz administrować.

2. Wywołaj <xref:System.ServiceProcess.ServiceController.Start%2A> metodę, aby uruchomić usługę.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług systemu Windows](how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md)
