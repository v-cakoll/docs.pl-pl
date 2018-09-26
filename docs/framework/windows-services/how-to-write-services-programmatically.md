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
ms.openlocfilehash: 904a82a3cc725221defb6795bf813b8cbc490c41
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073583"
---
# <a name="how-to-write-services-programmatically"></a>Porady: programowane pisanie usług
Jeśli nie chcesz użyć szablonu projektu usługi Windows, można napisać własne usługi, ustawiając dziedziczenia i inne elementy infrastruktury. Programowo utworzyć usługę, należy wykonać kilka kroków, które szablon w przeciwnym razie będzie obsługiwać dla Ciebie:  
  
-   Należy zdefiniować klasie usługi, aby odziedziczyć po <xref:System.ServiceProcess.ServiceBase> klasy.  
  
-   Należy utworzyć `Main` metoda projekt usługi, który definiuje działanie usług i wywołania <xref:System.ServiceProcess.ServiceBase.Run%2A> metody na nich.  
  
-   Konieczne jest przesłonięcie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedur i wypełnij jakiegokolwiek kodu, który ma ich wykonywania.  
  
### <a name="to-write-a-service-programmatically"></a>Aby programowane pisanie usług  
  
1.  Utwórz pusty projekt, a następnie utwórz odwołanie do przestrzeni nazw niezbędne wykonaj następujące czynności:  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła i kliknij przycisk **Dodaj odwołanie**.  
  
    2.  Na **.NET Framework** karty, przewiń do **System.dll** i kliknij przycisk **wybierz**.  
  
    3.  Przewiń do **System.ServiceProcess.dll** i kliknij przycisk **wybierz**.  
  
    4.  Kliknij przycisk **OK**.  
  
2.  Dodaj klasę i skonfiguruj ją, aby dziedziczyć <xref:System.ServiceProcess.ServiceBase>:  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  Dodaj następujący kod, aby skonfigurować klasie usługi:  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  Utwórz `Main` metody dla swojej klasy i użyj go do zdefiniowania usługi będzie zawierać klasy; `userService1` jest nazwa klasy:  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i zdefiniuj jakiegokolwiek przetwarzania, które ma być wykonywana po uruchomieniu usługi.  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  Zastąpienie wszelkich innych metod, które użytkownik chce zdefiniować niestandardowe przetwarzanie i pisanie kodu w celu ustalenia, jakie działania, które usługa należy wykonać w każdym przypadku.  
  
7.  Dodanie niezbędnych instalatorów dla aplikacji usługi. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
8.  Kompilowanie projektu przez wybranie **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
    > [!NOTE]
    >  Nie wciskaj F5, aby uruchomić projekt — nie można uruchomić projektu usługi w ten sposób.  
  
9. Tworzenie projektu Instalatora i akcje niestandardowe, aby zainstalować usługę. Aby uzyskać przykład, zobacz [wskazówki: tworzenie aplikacji usługi Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
10. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Instrukcje: rejestrowanie informacji o usługach](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
