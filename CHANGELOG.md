## 1.3.4(2017-11-02)

- Update Gradle plugin. Fix Nullable annotation in getBinding().

## 1.3.3(2017-08-21)

- Fix issue where viewmodels with generic types would not work correctly. 

## 1.3.2(2017-08-21)

- Updated dependencies (Support library, build tools, gradle)

## 1.3.1(2017-02-20)

- Critical issue fixed that was introduced two days ago in 1.3.0 - please update to 1.3.1 (issue is related to the new getViewOptional() method).

## 1.3.0(2017-02-18)

- Added ``getViewOptional()`` method which is guaranteed to be non-null. It will return a dummy implemenation in case the View is not null.
- Removed the need to override ```getViewModelClass```, the ViewModel class is now automatically extracted from the ViewModel class definition.

## 1.2.3(2017-01-4)

- Fix ProGuard settings.

## 1.2.2(2017-01-02)

- Remove wrong jetbrains annotations import. 

## 1.2.1(2016-12-08)

- Added default (null) implementation of ```getViewModelConfig()``` to the ```ViewModelBaseActivity``` so you don't need to implement it for your Activities. 

## 1.2.0(2016-11-24)

- Added better support for FragmentStatePagerAdapter by adding [ViewModelStatePagerAdapter.java](library/src/main/java/eu/inloop/viewmodel/support/ViewModelStatePagerAdapter.java).
- <b>Breaking change</b>: Added ```removeViewModel()``` to [IView](library/src/main/java/eu/inloop/viewmodel/IView.java). You don't need to make any changes if you are using the default ViewModelBaseFragment. Otherwise you need to implement this method and return null in case you don't need data binding.

## 1.1.0(2016-11-24)

- Added support for data binding
- <b>Breaking change</b>: Added ```getViewModelConfig()``` to [IView](library/src/main/java/eu/inloop/viewmodel/IView.java). You don't need to make any changes if you are using the default ViewModelBaseFragment. Otherwise you need to implement this method and return null in case you don't need data binding.

## 1.0.1(2016-9-14)
  
  - Updated dependencies (gradle, build tools, support library). 

## 1.0.0(2016-05-02)

  - We decided it's time for 1.0.0 release after a lot of use in production projects.
  - Made getViewModel() as NonNull to prevent a lot of unncessary null checks. It will now throw an IllegalStateException in case it's null (should not happen under normal conditions. Only if you call it too soon - before Activity.onCreate or Fragment.onCreate).
  - <b>Breaking change</b>: AbstractViewModel method saveState was renamed to onSaveInstanceState, bindView to onBindView and onModelRemoved to onDestroy. You may need to update your Models if you are overriding those methods.
  
## 0.4.1(2016-01-22)

  - Added ViewModelBaseEmptyActivity - which you can extend in case you don't need a ViewModel in your activity (but your fragments have ViewModels).
  - Added a sanity check if setModelView() was called - an error will be logged in case you forget to call it.
  
## 0.4.0(2016-01-19)

  - The ViewModel instances are now kept within the Activity (onRetainCustomNonConfigurationInstance). All ViewModels in the activity (including fragment ViewModels) will be cleared if you leave the activity.
  - If you are not extending ViewModelBaseActivity and instead you are using your own implementation, then you need to update your base Activity. The ViewModelBaseActivity.onCreate() changed and the activity now implements IViewModelProver interface.
  
## 0.3.2(2015-05-18)

Breaking changes:

  - Add setModelView() method which has to be called in every Fragment/Activity after the view was initialized. This is usually on the end of onCreate / onViewCreated - [commit](https://github.com/inloop/AndroidViewModel/commit/54a7d1a96d38d1a17c8bc7c81b081d52064bde28)

## 0.3.1(2015-05-14)

Bugfixes:

  - Fix ViewModel ID clashes after the application was restored due to low memory - [commit](https://github.com/inloop/AndroidViewModel/commit/cecfd54d3008c07c19ad7685b97e9fe2acb5c369)
