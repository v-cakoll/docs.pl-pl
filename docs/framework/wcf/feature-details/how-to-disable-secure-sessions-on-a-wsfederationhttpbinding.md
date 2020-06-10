---
title: 'Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: df057d64feb89d1e43b938b36cb48f2f103b17d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595391"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding

Niektóre usługi mogą wymagać poświadczeń federacyjnych, ale nie obsługują bezpiecznych sesji. W takim przypadku należy wyłączyć funkcję bezpiecznej sesji. W przeciwieństwie do <xref:System.ServiceModel.WSHttpBinding> klasy, Klasa nie pozwala <xref:System.ServiceModel.WSFederationHttpBinding> na wyłączenie bezpiecznych sesji podczas komunikacji z usługą. Zamiast tego należy utworzyć niestandardowe powiązanie, które zastępuje ustawienia bezpiecznej sesji przy użyciu Bootstrap.

W tym temacie pokazano, jak modyfikować elementy powiązania zawarte w elemencie w <xref:System.ServiceModel.WSFederationHttpBinding> celu utworzenia niestandardowego powiązania. Wynik jest identyczny z <xref:System.ServiceModel.WSFederationHttpBinding> tą różnicą, że nie używa bezpiecznych sesji.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Aby utworzyć niestandardowe powiązanie federacyjne bez bezpiecznej sesji

1. Utwórz wystąpienie klasy jako bezwzględnie <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie lub przez załadowanie jednego z pliku konfiguracji.

2. Klonowanie <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding> .

3. Znajdź <xref:System.ServiceModel.Channels.SecurityBindingElement> w <xref:System.ServiceModel.Channels.CustomBinding> .

4. Znajdź <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> w <xref:System.ServiceModel.Channels.SecurityBindingElement> .

5. Zastąp oryginał <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem powiązania zabezpieczeń Bootstrap z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .

## <a name="example"></a>Przykład

Poniższy przykład powoduje utworzenie niestandardowego powiązania federacyjnego bez bezpiecznej sesji.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

- Aby skompilować przykład kodu, Utwórz projekt, który odwołuje się do zestawu System. ServiceModel. dll.

## <a name="see-also"></a>Zobacz też

- [Wiązania i zabezpieczenia](bindings-and-security.md)
