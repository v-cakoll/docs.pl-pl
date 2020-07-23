---
title: 'Instrukcje: Programowane pisanie usług'
description: Zobacz, jak programowo pisać usługi, konfigurując dziedziczenie i inne elementy infrastruktury samodzielnie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: 9693e3d387f38319519ab04211d8219fe1e5dda1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925712"
---
# <a name="how-to-write-services-programmatically"></a>Instrukcje: Programowane pisanie usług
Jeśli zdecydujesz się nie używać szablonu projektu usługi systemu Windows, możesz napisać własne usługi, konfigurując dziedziczenie i inne elementy infrastruktury samodzielnie. W przypadku programistycznego tworzenia usługi należy wykonać kilka czynności, dla których szablon mógłby obsłużyć:  
  
- Należy skonfigurować klasę usługi, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase> klasy.  
  
- Należy utworzyć `Main` metodę dla projektu usługi, który definiuje usługi do uruchomienia i wywołuje <xref:System.ServiceProcess.ServiceBase.Run%2A> metodę z nich.  
  
- Należy zastąpić <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedury i wprowadzić dowolny kod, który ma zostać uruchomiony.  
  
### <a name="to-write-a-service-programmatically"></a>Aby programowo napisać usługę  
  
1. Utwórz pusty projekt i Utwórz odwołanie do odpowiednich przestrzeni nazw, wykonując następujące czynności:  
  
    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i kliknij polecenie **Dodaj odwołanie**.  
  
    2. Na karcie **.NET Framework** przewiń do **System.dll** i kliknij pozycję **Wybierz**.  
  
    3. Przewiń do **System.ServiceProcess.dll** i kliknij przycisk **Wybierz**.  
  
    4. Kliknij przycisk **OK**.  
  
2. Dodaj klasę i skonfiguruj ją, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase> :  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. Dodaj następujący kod, aby skonfigurować klasę usługi:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. Utwórz `Main` metodę dla klasy i użyj jej do zdefiniowania usługi, która będzie zawierała Klasa; `userService1` jest nazwą klasy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodę i zdefiniuj wszelkie przetwarzanie, które mają być wykonywane, gdy usługa zostanie uruchomiona.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. Zastąp wszystkie inne metody, dla których chcesz zdefiniować niestandardowe przetwarzanie, i napisz kod, aby określić działania, które usługa powinna wykonać w każdym przypadku.  
  
7. Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md).  
  
8. Skompiluj projekt, wybierając opcję **Kompiluj rozwiązanie** w menu **kompilacja** .  
  
    > [!NOTE]
    > Nie należy naciskać klawisza F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
9. Utwórz projekt konfiguracji i akcje niestandardowe w celu zainstalowania usługi. Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Tworzenie usług systemu Windows](how-to-create-windows-services.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](how-to-add-installers-to-your-service-application.md)
- [Instrukcje: Rejestrowanie informacji o usługach](how-to-log-information-about-services.md)
- [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
