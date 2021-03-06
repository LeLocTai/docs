---
title: "How to: Customize Data Binding Behaviors (WCF Data Services)"
ms.date: "03/30/2017"
dev_langs: 
  - "csharp"
  - "vb"
helpviewer_keywords: 
  - "WCF Data Services, customizing"
  - "WCF Data Services, data binding"
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
---
# How to: Customize Data Binding Behaviors (WCF Data Services)
With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can supply custom logic that is called by the <xref:System.Data.Services.Client.DataServiceCollection%601> when an object is added or removed from the binding collection or when a property change is detected. This custom logic is provided as methods, referenced as <xref:System.Func%602> delegates, that return a value of `false` when the default behavior should still be performed when the custom method completes and `true` when subsequent processing of the event should be stopped.  
  
 The examples in this topic supply custom methods for both the `entityChanged` and `entityCollectionChanged` parameters of <xref:System.Data.Services.Client.DataServiceCollection%601>. The examples in this topic use the Northwind sample data service and autogenerated client data service classes. This service and the client data classes are created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Example  
 The following code-behind page for the XAML file creates a <xref:System.Data.Services.Client.DataServiceCollection%601> with custom methods that are called when changes occur to data that is bound to the binding collection. When the <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> event occurs, the supplied method prevents an item that has been removed from the binding collection from being deleted from the data service. When the <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> event occurs, the `ShipDate` value is validated to ensure that changes are not made to orders that have already shipped.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## Example  
 The following XAML defines the window for the previous example.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## See Also  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
