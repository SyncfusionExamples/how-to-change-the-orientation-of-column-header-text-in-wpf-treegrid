# How to change the orientation of column header text in wpf treegrid?

This example illustrates how to change the orientation of column header text in [WPF TreeGrid](https://www.syncfusion.com/wpf-controls/treegrid).

Orientation of the `TreeGrid` column header text can be changed by editing the control template of the [TreeGridHeaderCell](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.TreeGrid.TreeGridHeaderCell.html) and applying `RotateTransform`.


``` xml
<Style TargetType="syncfusion:TreeGridHeaderCell">
    <Setter Property="Background" Value="{StaticResource HeaderBackgroundBrush}" />
    <Setter Property="Foreground" Value="{StaticResource HeaderForegroundBrush}" />
    <Setter Property="BorderBrush" Value="{StaticResource HeaderBorderBrush}" />
    <Setter Property="BorderThickness" Value="0,0,1,1" />
    <Setter Property="HorizontalContentAlignment" Value="Center" />
    <Setter Property="Padding" Value="5,3,5,3" />
    <Setter Property="FontSize" Value="14" />
    <Setter Property="FontWeight" Value="Normal" />
    <Setter Property="IsTabStop" Value="False" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:TreeGridHeaderCell">
                <Grid>
                    <Grid.LayoutTransform>
                        <RotateTransform Angle="90"/>
                    </Grid.LayoutTransform>
                    <Border x:Name="PART_FooterCellBorder"
                        Background="{TemplateBinding Background}"
                        BorderBrush="{TemplateBinding BorderBrush}" />
                    <Border x:Name="PART_HeaderCellBorder"
                        Background="{TemplateBinding Background}"
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}"
                        SnapsToDevicePixels="True">
                        <Grid Margin="{TemplateBinding Padding}" SnapsToDevicePixels="True">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="*" />
                                <ColumnDefinition Width="Auto" />
                            </Grid.ColumnDefinitions>
                            <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}"
                                            VerticalAlignment="Center"
                                            Focusable="False" />
                            <Grid x:Name="PART_SortButtonPresenter"
                                Grid.Column="1"
                                SnapsToDevicePixels="True">
                                <Grid.ColumnDefinitions>
                                    <ColumnDefinition Width="0" MinWidth="{Binding Path=SortDirection, Mode=OneWay, RelativeSource={RelativeSource TemplatedParent}, Converter={StaticResource sortDirectionToWidthConverter}}" />
                                    <ColumnDefinition Width="*" />
                                </Grid.ColumnDefinitions>

                                <Path Width="8.938"
                                    Height="8.138"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    Data="F1M753.644,-13.0589L753.736,-12.9639 753.557,-12.7816 732.137,8.63641 732.137,29.7119 756.445,5.40851 764.094,-2.24384 764.275,-2.42352 771.834,5.1286 796.137,29.4372 796.137,8.36163 774.722,-13.0589 764.181,-23.5967 753.644,-13.0589z"
                                    Fill="{TemplateBinding Foreground}"
                                    SnapsToDevicePixels="True"
                                    Stretch="Fill"
                                    Visibility="{Binding Path=SortDirection,
                                                        RelativeSource={RelativeSource TemplatedParent},
                                                        ConverterParameter=Ascending,
                                                        Converter={StaticResource sortDirectionToVisibilityConverter}}">
                                    <Path.RenderTransform>
                                        <TransformGroup>
                                            <TransformGroup.Children>
                                                <RotateTransform Angle="0" />
                                                <ScaleTransform ScaleX="1" ScaleY="1" />
                                            </TransformGroup.Children>
                                        </TransformGroup>
                                    </Path.RenderTransform>
                                </Path>

                                <Path Width="8.938"
                                    Height="8.138"
                                    HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    Data="F1M181.297,177.841L181.205,177.746 181.385,177.563 202.804,156.146 202.804,135.07 178.497,159.373 170.847,167.026 170.666,167.205 163.107,159.653 138.804,135.345 138.804,156.42 160.219,177.841 170.76,188.379 181.297,177.841z"
                                    Fill="{TemplateBinding Foreground}"
                                    SnapsToDevicePixels="True"
                                    Stretch="Fill"
                                    Visibility="{Binding Path=SortDirection,
                                                        RelativeSource={RelativeSource TemplatedParent},
                                                        ConverterParameter=Decending,
                                                        Converter={StaticResource sortDirectionToVisibilityConverter}}">
                                    <Path.RenderTransform>
                                        <TransformGroup>
                                            <TransformGroup.Children>
                                                <RotateTransform Angle="0" />
                                                <ScaleTransform ScaleX="1" ScaleY="1" />
                                            </TransformGroup.Children>
                                        </TransformGroup>
                                    </Path.RenderTransform>
                                </Path>

                                <TextBlock Grid.Column="1"
                                        Margin="0,-4,0,0"
                                        VerticalAlignment="Center"
                                        FontSize="10"
                                        Foreground="{TemplateBinding Foreground}"
                                        SnapsToDevicePixels="True"
                                        Text="{TemplateBinding SortNumber}"
                                        Visibility="{TemplateBinding SortNumberVisibility}" />

                            </Grid>
                        </Grid>
                    </Border>
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
```