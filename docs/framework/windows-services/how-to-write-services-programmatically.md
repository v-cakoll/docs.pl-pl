---
title: 'Porady: programowane pisanie usług'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
manager: douge
ms.openlocfilehash: 99fd44723bba21127e2a5e0ba3e9bfc4b90b52d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-services-programmatically"></a>Porady: programowane pisanie usług
Jeśli wybierzesz nie użyć szablonu projektu usługi systemu Windows, można napisać własny usług przez ustawienie dziedziczenia i inne elementy infrastruktury. Podczas tworzenia usługi programowo, należy wykonać kilka kroków, które szablonu może obsłużyć w inny sposób można:  
  
-   Należy skonfigurować klasie usługi odziedziczone <xref:System.ServiceProcess.ServiceBase> klasy.  
  
-   Należy utworzyć `Main` metody dla projektu usługi, który definiuje działanie usług i wywołania <xref:System.ServiceProcess.ServiceBase.Run%2A> metody na nich.  
  
-   Konieczne jest przesłonięcie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i wypełnij żadnego kodu mają się uruchomić.  
  
### <a name="to-write-a-service-programmatically"></a>Programowo zapisu usługi  
  
1.  Utwórz pusty projekt i utworzyć odwołania do przestrzeni nazw niezbędne wykonaj następujące czynności:  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł i kliknij przycisk **Dodaj odwołanie**.  
  
    2.  Na **.NET Framework** karcie, przewiń do **System.dll** i kliknij przycisk **wybierz**.  
  
    3.  Przewiń do **System.ServiceProcess.dll** i kliknij przycisk **wybierz**.  
  
    4.  Kliknij przycisk **OK**.  
  
2.  Dodaj klasę i skonfigurować go, aby dziedziczyć z <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Dodaj następujący kod, aby skonfigurować klasie usługi:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Utwórz `Main` metody dla klasy i użyj go do zdefiniowania usługi będzie zawierać klasy; `userService1` jest nazwą klasy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i zdefiniuj jakiegokolwiek przetwarzania, które ma być wykonywana po uruchomieniu usługi.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Zastąpienie innych metod, które chcesz zdefiniować niestandardowe przetwarzania dla i napisać kod, aby określić akcje, które usługi należy wykonać w każdym przypadku.  
  
7.  Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Tworzenie projektu, wybierając **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Nie naciśnij klawisz F5, aby uruchomić projekt — nie można uruchomić projekt usługi w ten sposób.  
  
9. Tworzenie projektu Instalatora i akcje niestandardowe, aby zainstalować usługi. Na przykład zobacz [wskazówki: tworzenie aplikacji usługi systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Instrukcje: rejestrowanie informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
