---
title: 'Instrukcje: Programowane pisanie usług'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 29e0b95ad91c93f3a23246daf2be128b10d7e2ce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952405"
---
# <a name="how-to-write-services-programmatically"></a>Instrukcje: Programowane pisanie usług
Jeśli zdecydujesz się nie używać szablonu projektu usługi systemu Windows, możesz napisać własne usługi, konfigurując dziedziczenie i inne elementy infrastruktury samodzielnie. W przypadku programistycznego tworzenia usługi należy wykonać kilka czynności, dla których szablon mógłby obsłużyć:  
  
- Należy skonfigurować klasę usługi, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase> klasy.  
  
- Należy utworzyć `Main` metodę dla projektu usługi, który definiuje usługi do uruchomienia i <xref:System.ServiceProcess.ServiceBase.Run%2A> wywołuje metodę z nich.  
  
- Należy zastąpić <xref:System.ServiceProcess.ServiceBase.OnStart%2A> procedury i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> wprowadzić dowolny kod, który ma zostać uruchomiony.  
  
### <a name="to-write-a-service-programmatically"></a>Aby programowo napisać usługę  
  
1. Utwórz pusty projekt i Utwórz odwołanie do odpowiednich przestrzeni nazw, wykonując następujące czynności:  
  
    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i kliknij polecenie **Dodaj odwołanie**.  
  
    2. Na karcie **.NET Framework** przewiń do **pliku System. dll** , a następnie kliknij przycisk **Wybierz**.  
  
    3. Przewiń do **pliku System. ServiceProcess. dll** , a następnie kliknij pozycję **Wybierz**.  
  
    4. Kliknij przycisk **OK**.  
  
2. Dodaj klasę i skonfiguruj ją, aby dziedziczyć <xref:System.ServiceProcess.ServiceBase>z:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Dodaj następujący kod, aby skonfigurować klasę usługi:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. `Main` Utwórz metodę dla klasy i użyj jej do zdefiniowania usługi, która będzie zawierać Klasa; `userService1` jest nazwą klasy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę i zdefiniuj wszelkie przetwarzanie, które mają być wykonywane, gdy usługa zostanie uruchomiona.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Zastąp wszystkie inne metody, dla których chcesz zdefiniować niestandardowe przetwarzanie, i napisz kod, aby określić działania, które usługa powinna wykonać w każdym przypadku.  
  
7. Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)usługi.  
  
8. Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .  
  
    > [!NOTE]
    > Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
9. Utwórz projekt konfiguracji i akcje niestandardowe w celu zainstalowania usługi. Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)składników.  
  
10. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)usług.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Rejestruj informacje o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
